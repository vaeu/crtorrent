# crtorrent

## Overview

`crtorrent` is a simple utility written in POSIX sh that, with the help
of `mktorrent`, creates private torrent files for one or more
directories given as arguments.

## What’s the point if `mktorrent` already exists?

As of version 1.1, `mktorrent` does not automatically determine the
piece length based on the size of a directory, whereas `crtorrent` does
exactly that.

## Dependencies

The one and only dependency is `mktorrent`.

## Usage

```
crtorrent DIR1 [DIR2..]
```

`crtorrent` takes one or more directories as arguments and produces a
torrent file for each processed directory, embedding both the announce
URL of chosen private tracker as well as its source string into each
meta-info file.

All private trackers provide users with their unique announce URL that
can be put into the `announce` variable right at the beginning of this
script. Most, if not all, private trackers require users to embed an
abbreviation of the tracker’s name into torrent meta-files that usually
consists of three upper case letters, such as ~~NSA,~~ RED, OPS, JPS and
others; likewise, the `src` variable at the beginning of the script can
be modified to include said abbreviation by editing the file directly
using text editor of your choice.

## Examples

Set custom announce URL using `sed`:

```
sed -i '/^announce/ s,",&https://example.com/abc0d12e3/announce,' /path/to/crtorrent
```

Set ‘RED’ as primary source tag using `sed`:

```
sed -i '/^src/ s,",&RED,' /path/to/crtorrent
```
