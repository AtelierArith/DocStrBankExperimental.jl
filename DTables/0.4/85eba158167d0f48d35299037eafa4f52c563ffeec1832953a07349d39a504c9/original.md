```
DTable(loader_function, files::Vector{String}; tabletype=nothing)
```

Constructs a `DTable` using a list of filenames and a `loader_function`. Partitioning is based on the contents of the files provided, which means that one file is used to create one partition.

Providing `tabletype` kwarg overrides the internal table partition type.
