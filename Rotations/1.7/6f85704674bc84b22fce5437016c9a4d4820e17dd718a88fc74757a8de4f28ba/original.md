```
struct Angle2dGenerator{T} <: RotationGenerator{2,T}
    v::T
end
```

A 2×2 rotation generator matrix (i.e. skew-symmetric matrix). [ 0 -v   v  0 ]
