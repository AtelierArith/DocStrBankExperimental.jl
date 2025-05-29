```
rotate(M, θ)
```

Rotates the component represented by the Mueller matrix `M` counter-clockwise by angle `θ` (in radians).

# Examples

```jldoctest
julia> M = linear_polarizer();

julia> Mr = rotate(M, π/2);

julia> Mr ≈ linear_polarizer(π/2)
true
```

# See also

[`Mueller.rotation`](@ref)
