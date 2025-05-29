```
`pglib(fname::AbstractString)`

open a matpower case file from the IEEE PGlib opf libray.  If the exact file
cannot be found, then the cases will be filtered.  If a single case
contains the name, it will be opened.
```
