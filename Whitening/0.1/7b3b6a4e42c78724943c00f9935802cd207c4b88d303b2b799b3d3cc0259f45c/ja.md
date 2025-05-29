```
ZCA{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

ゼロ位相成分分析 (ZCA) ホワイトニング変換。

共分散行列 $Σ$ が与えられたとき、ホワイトニング行列は $W = Σ^{-\frac{1}{2}}$ です。
