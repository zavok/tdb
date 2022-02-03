# Tag Database

This is a system for managing tag <-> file associations. It consists of
two files, `tags` and `sha`, and a script `tdb`.

`sha` stores lines of sha1 hashes and filenames, separated by two
spaces, as emitted by `sha1sum(1)`.

`tags` stores lines of tag names and sha1 hashes, separated by a
tab symbol.

`tdb` manipulates these files to perform tag based searches.

## Install

There's no install. Just drop `tdb` in a directory with your files,
and launch it from there.

## Dependencies

`tdb` is writen in `rc(1)` shell script. It's provided by `plan9port`

## Usage

Generate sha file:

	$ ./tdb hash photos > sha

Tag a file:

	$ ./tdb tag photos/joe.jpg joe friend night beer my_car

Untag a file:

	$ ./tdb untag photos/joe.jpg friend

Look for files:

	$ ./tdb get joe
	photos/joe.jpg
	photos/crash.jpg
	photos/hospital.jpg

Combine it with `sxiv(1)`:

	$ ./tdb get landscape | sxiv -it

## Bugs

- Tagging files is too much work.
- `tdb` might require slight modifications to work on plan9
- tree walk code in `hash` function might break if your directory tree is too big.

