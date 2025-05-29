```
struct MPO{O,V<:AbstractVector{O}} <: AbstractMPO{O}
```

線形順序を持つテンソル積空間上で作用する行列積演算子 (MPO)。

関連情報: [`FiniteMPO`](@ref), [`InfiniteMPO`](@ref)
