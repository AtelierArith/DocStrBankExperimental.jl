```
labels(x::ComponentVector)
```

Get string labels for for each index of a `ComponentVector`. Useful for automatic plot legend labelling.

# Examples

```jldoctest
julia> x = ComponentArray(a=5, b=[(a=(a=20,b=1), b=0), (a=(a=33,b=1), b=0)], c=(a=(a=2, b=[1,2]), b=[1. 2.; 5 6]))
ComponentVector{Float64}(a = 5.0, b = ComponentVector{Float64, SubArray{Float64, 1, Vector{Float64}, Tuple{UnitRange{Int64}}, true}, Tuple{Axis{(a = ViewAxis(1:2, Axis(a = 1, b = 2)), b = 3)}}}[(a = (a = 20.0, b = 1.0), b = 0.0), (a = (a = 33.0, b = 1.0), b = 0.0)], c = (a = (a = 2.0, b = [1.0, 2.0]), b = [1.0 2.0; 5.0 6.0]))

julia> ComponentArrays.labels(x)
14-element Vector{String}:
 "a"
 "b[1].a.a"
 "b[1].a.b"
 "b[1].b"
 "b[2].a.a"
 "b[2].a.b"
 "b[2].b"
 "c.a.a"
 "c.a.b[1]"
 "c.a.b[2]"
 "c.b[1,1]"
 "c.b[2,1]"
 "c.b[1,2]"
 "c.b[2,2]"
```

see also [`label2index`](@ref)
