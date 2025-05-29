```
GeometricBeam(w=0.0, k=0.0, z=0.0)
```

Defines a geometrical ray beam with keywords. Distance to the axis is `w`, the angle with respect to the axis is `k`. `zpos` is the initial position along the optical axis.

See also [`GaussianBeam`](@ref).

## Example

```jldoctest
julia> GeometricBeam(w=1.0)
GeometricBeam{Float64}(1.0, 0.0, 0.0)
```
