This module provides ways to parse and write files in [FASTA format](http://en.wikipedia.org/wiki/FASTA_format) in Julia. It is designed to be lightweight and fast; the parsing method is inspired by [kseq.h](http://lh3lh3.users.sourceforge.net/kseq.shtml). It can read and write files on the fly, keeping only one entry at a time in memory, and it can read and write gzip-compressed files.

See [`FastaReader`](@ref), [`FastaWriter`](@ref), [`readfasta`](@ref), [`writefasta`](@ref), [`readentry`](@ref) and [`writeentry`](@ref).
