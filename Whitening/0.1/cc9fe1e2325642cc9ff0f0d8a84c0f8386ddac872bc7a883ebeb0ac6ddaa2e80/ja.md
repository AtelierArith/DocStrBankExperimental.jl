```
PCA{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

主成分分析 (PCA) ホワイトニング変換。

共分散行列の固有分解が与えられたとき、$Σ = UΛUᵀ$、ホワイトニング行列は $W = Λ^{-\frac{1}{2}}Uᵀ$ です。
