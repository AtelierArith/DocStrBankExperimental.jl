```
Rotate(R)
```

Rotate geometry or domain with rotation `R` from Rotations.jl.

```
Rotate(u, v)
```

Rotation mapping the axis directed by `u` to the axis directed by `v`.  More precisely, it maps the plane passing through the origin with normal  vector `u` to the plane passing through the origin with normal vector `v`.

```
Rotate(θ)
```

Rotate the 2D geometry or domain by angle `θ`, in radians, using the `Angle2d` rotation.

## Examples

```julia
Rotate(one(RotXYZ{Float64})) # identity rotation
Rotate(AngleAxis(0.2, 1.0, 0.0, 0.0)) # rotate 0.2 radians around X axis
Rotate(rand(QuatRotation{Float64})) # random rotation
Rotate(Vec(1, 0, 0), Vec(1, 1, 1)) # rotation from (1, 0, 0) to (1, 1, 1)
Rotate(π / 2) # 2D rotation with angle in radians
```
