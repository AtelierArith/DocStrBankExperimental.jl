```
ZCAcor{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

スケール不変ゼロ位相成分分析 (ZCA-cor) ホワイトニング変換。

相関行列 $P$ と対角分散行列 $V$ が与えられたとき、ホワイトニング行列は $W = P^{-\frac{1}{2}}V^{-\frac{1}{2}}$ です。
