```
pload(dir::AbstractString, ranks::AbstractArray{<:Integer})
```

Load a partitioned object stored in a set of JLD2 files in directory `dir` indexed by MPI ranks `ranks`.
