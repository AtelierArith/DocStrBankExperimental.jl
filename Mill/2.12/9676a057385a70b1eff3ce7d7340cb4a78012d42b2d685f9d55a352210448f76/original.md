```
datasummary(n::AbstractMillNode)
```

Print summary of parameters of node `n`.

# Examples

```jldoctest
julia> n = ProductNode(ArrayNode(randn(2, 3)))
ProductNode  3 obs
  ╰── ArrayNode(2×3 Array with Float64 elements)  3 obs

julia> datasummary(n)
"Data summary: 3 obs, 104 bytes."
```

See also: [`modelsummary`](@ref).
