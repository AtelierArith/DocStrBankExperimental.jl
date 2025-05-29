```
eulerRotationMat(θ::FT, ϕ::FT, unit::Symbol) where{FT<:AbstractFloat}
```

计算转到给定指向 `θ, ϕ` 处的旋转矩阵，旋转一步到位，不发生自旋。
