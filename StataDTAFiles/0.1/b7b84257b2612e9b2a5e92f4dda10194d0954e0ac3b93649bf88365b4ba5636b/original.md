```julia
struct DTAFile{T<:NamedTuple, B<:StataDTAFiles.ByteOrderIO}
```

Representation of a Stata DTA file for which everything except the data itself has been read.

The data (rows) can be read as `NamedTuple`s, using the iteration interface.
