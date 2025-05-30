```
whiten(K::AbstractWhiteningTransform{T}, x::AbstractVector{T}) where {T<:Base.IEEEFloat}
```

`x`をホワイトニングされたベクトルに変換します。すなわち、`z = W * (x - μ)`、変換カーネル`K`を使用します。

もし`K`が`n ↦ p`を圧縮するなら、`z ∈ ℝᵖ`です。
