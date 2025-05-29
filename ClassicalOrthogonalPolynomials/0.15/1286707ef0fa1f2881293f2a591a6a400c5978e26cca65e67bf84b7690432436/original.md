```
LegendreWeight{T}()
LegendreWeight()
```

The quasi-vector representing the Legendre weight function (const 1) on [-1,1]. See also [`legendreweight`](@ref) and [`Legendre`](@ref).

# Examples

```jldoctest
julia> w = LegendreWeight()
LegendreWeight{Float64}()

julia> w[0.5]
1.0

julia> axes(w)
(Inclusion(-1.0 .. 1.0 (Chebyshev)),)
```
