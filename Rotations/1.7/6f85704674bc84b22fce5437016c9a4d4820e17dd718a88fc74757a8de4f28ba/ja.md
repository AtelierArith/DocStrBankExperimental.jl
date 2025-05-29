```
struct Angle2dGenerator{T} <: RotationGenerator{2,T}
    v::T
end
```

2×2 回転生成器行列（すなわち、斜対称行列）。 [ 0 -v   v  0 ]
