```
PCAcor{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

スケール不変主成分分析（PCA-cor）ホワイトニング変換。

相関行列の固有分解が $P = GΘGᵀ$ であり、対角分散行列が $V$ の場合、ホワイトニング行列は $W = Θ^{-\frac{1}{2}}GᵀV^{-\frac{1}{2}}$ となります。
