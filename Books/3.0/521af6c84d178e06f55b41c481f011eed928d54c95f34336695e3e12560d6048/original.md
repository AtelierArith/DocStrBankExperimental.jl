```
entr_gen(
    path::Union{AbstractString,Regex},
    [block_number];
    M=[],
    kwargs...
)
```

Execute `gen(path, [block_number]; M, kwargs...)` whenever files in `contents` or code in one of the modules `M` changes. This is a convenience function around `Revise.entr(() -> gen(...), ["contents"], M)`.

# Example

```
julia> entr_gen("plots"; M=[MyModule])
[...]

julia> entr_gen(r"plot*"; M=[MyModule])
[...]
```
