```
wrapdims(::NamedTuple)
wrapdims(::NamedTuple, ::Symbol)
```

Converts the `NamedTuple`'s keys into those of a one-dimensional `KeyedArray`. If a dimension name is provided, the this adds a `NamedDimsArray` wrapper too.

# Examples

```jldoctest
julia> wrapdims((alpha=1, beta=20))
1-dimensional KeyedArray(...) with keys:
↓   2-element Vector{Symbol}
And data, 2-element Vector{Int64}:
 (:alpha)   1
 (:beta)   20

julia> push!(ans, :gamma => 300)
1-dimensional KeyedArray(...) with keys:
↓   3-element Vector{Symbol}
And data, 3-element Vector{Int64}:
 (:alpha)    1
 (:beta)    20
 (:gamma)  300
```
