```
Chol{T<:Base.IEEEFloat} <: AbstractWhiteningTransform{T}
```

コレスキーホワイトニング変換。

逆共分散行列のコレスキー分解に基づいて、$Σ⁻¹ = LLᵀ$ が与えられるとき、ホワイトニング行列は $W = Lᵀ$ です。
