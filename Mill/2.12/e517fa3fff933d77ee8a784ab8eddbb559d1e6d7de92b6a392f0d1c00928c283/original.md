```
modelsummary(m::AbstractMillModel)
```

Print summary of parameters of model `m`.

# Examples

```jldoctest
julia> m = ProductModel(ArrayModel(Dense(2, 3)))
ProductModel ↦ identity
  ╰── ArrayModel(Dense(2 => 3))  2 arrays, 9 params, 124 bytes

julia> modelsummary(m)
"Model summary: 2 arrays, 9 params, 124 bytes"
```

See also: [`datasummary`](@ref).
