```
valkeys(x::ComponentVector)
valkeys(x::AbstractAxis)
```

Returns `Val`-wrapped keys of `ComponentVector` for fast iteration over component keys. Also works directly on an `AbstractAxis`.

# Examples

```jldoctest
julia> using ComponentArrays

julia> ca = ComponentArray(a=1, b=[1,2,3], c=(a=4,))
ComponentVector{Int64}(a = 1, b = [1, 2, 3], c = (a = 4))

julia> [ca[k] for k in valkeys(ca)]
3-element Vector{Any}:
 1
  [1, 2, 3]
  ComponentVector{Int64}(a = 4)

julia> sum(prod(ca[k]) for k in valkeys(ca))
11
```
