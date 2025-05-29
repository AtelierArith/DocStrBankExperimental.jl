```
uweights(s::Integer)
uweights(::Type{T}, s::Integer) where T<:Real
```

Construct a `UnitWeights` vector with length `s` and weight elements of type `T`. All weight elements are identically one.

# Examples

```julia-repl
julia> uweights(3)
3-element UnitWeights{Int64}:
 1
 1
 1

julia> uweights(Float64, 3)
3-element UnitWeights{Float64}:
 1.0
 1.0
 1.0
```
