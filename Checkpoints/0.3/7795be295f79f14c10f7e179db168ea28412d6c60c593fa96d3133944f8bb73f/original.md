```
index_checkpoint_files(dir)
```

Constructs a index for all the files output by checkpoints located within  `dir`. This index tells you their checkpoint*name, checkpoint*path, tags, etc. See [`IndexEntry`](@ref) for full information on what is recorded.

Handily, a `Vector{IndexEntry}` is a valid [Tables.jl Table][1]. This means you can do `DataFrame(index_checkpoint_files(dir))` and get a nice easy to work with [DataFrame][2].

You can also work with it directly, say you wanted to get all checkpoints files for `forecasts` with the tag `model="Stage1"`. This would be something like:

```julia
[checkpoint_path(x) for x in index_checkpoint_files(dir) if x.checkpoint_name=="forecast" && x.model=="Stage1"]
```

1: https://github.com/JuliaData/Tables.jl 2: https://github.com/JuliaData/DataFrames.jl
