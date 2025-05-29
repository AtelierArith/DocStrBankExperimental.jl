```
struct RotationVecGenerator{T} <: RotationGenerator{2,T}
    x::T
    y::T
    z::T
end
```

3×3 回転生成器行列（すなわち、斜対称行列）。 [ 0 -z  y   z  0 -x  -y  x  0]
