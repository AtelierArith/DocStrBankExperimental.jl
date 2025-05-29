```
Acoustic{T<:AbstractFloat,Dim}(ρ::T, c::Complex{T})
Acoustic(ρ::T, c::Union{T,Complex{AbstractFloat}}, Dim::Integer)
```

波速 (c) と密度 (ρ) を持つ均質等方性音響媒体の物理特性

この媒体でのシミュレーションは、Dim 次元のスカラー (1D) フィールドを生成します。
