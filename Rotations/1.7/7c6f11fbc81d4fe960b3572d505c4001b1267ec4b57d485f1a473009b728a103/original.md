```
struct Angle2d{T} <: Rotation{2,T}
    theta::T
end
```

A 2×2 rotation matrix parameterized by a 2D rotation by angle. Only the angle is stored inside the `Angle2d` type, values of `getindex` etc. are computed on the fly.
