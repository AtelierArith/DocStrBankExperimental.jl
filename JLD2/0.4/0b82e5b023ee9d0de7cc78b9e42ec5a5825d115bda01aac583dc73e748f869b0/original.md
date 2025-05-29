```
jldsave(filename; kwargs...)
jldsave(filename, compress; kwargs...)
jldsave(filename, compress, iotype; kwargs...)
```

Creates a JLD2 file at `filename` and stores the variables given as keyword arguments.

# Examples

```julia
jldsave("example.jld2"; a=1, b=2, c)
```

is equivalent to

```julia
jldopen("example.jld2", "w") do f
    f["a"] = 1
    f["b"] = 2
    f["c"] = c
end
```

To choose the io type `IOStream` instead of the default `MmapIO` use  `jldsave(fn, IOStream; kwargs...)`.
