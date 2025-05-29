```
Chol{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

コレスキーホワイトニング変換。

逆共分散行列のコレスキー分解に基づいて、$Σ⁻¹ = LLᵀ$ が得られ、ホワイトニング行列 $W = Lᵀ$ となります。
