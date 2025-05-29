```
struct RotationVecGenerator{T} <: RotationGenerator{2,T}
    x::T
    y::T
    z::T
end
```

A 3×3 rotation generator matrix (i.e. skew-symmetric matrix). [ 0 -z  y   z  0 -x  -y  x  0]
