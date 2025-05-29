```
materialize(lines::LineIndex,  f::Function, rows::Union{UnitRange{Int}, Vector{Int}} = 1:length(lines); eltype = T where T)
```

Apply `f` to `rows` selected. `eltype` of result can be specified as keyword argument.
