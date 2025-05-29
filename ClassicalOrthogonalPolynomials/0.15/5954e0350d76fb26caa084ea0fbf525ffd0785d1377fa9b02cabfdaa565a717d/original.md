```
legendreweight(d::AbstractInterval)
```

The [`LegendreWeight`](@ref) affine-mapped to interval `d`.

# Examples

```jldoctest
julia> w = legendreweight(0..1)
LegendreWeight{Float64}() affine mapped to 0 .. 1

julia> axes(w)
(Inclusion(0 .. 1),)

julia> w[0]
1.0
```
