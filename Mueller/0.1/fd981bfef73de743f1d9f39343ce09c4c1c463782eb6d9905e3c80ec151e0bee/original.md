```
rotation([T=Float64], θ)
```

Generate a rotation matrix with the given angle, in radians, `θ`. This can be used to rotate the axes of polarization components arbitrarily. For convenience, the [`rotate`](@ref) method will rotate a component, without having to generate this matrix, itself.

# Examples

Rotate a linear polarizer by 90 degrees counter-clockwise

```jldoctest
julia> M = linear_polarizer();

julia> r = rotation(π/4);

julia> Mr = r' * M * r;

julia> Mr ≈ linear_polarizer(π/4)
true
```

# See also

[`rotate`](@ref)
