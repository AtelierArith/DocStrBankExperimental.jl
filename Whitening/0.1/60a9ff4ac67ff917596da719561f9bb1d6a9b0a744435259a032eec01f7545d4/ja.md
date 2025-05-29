```
whiten(K::AbstractWhiteningTransform{T}, x::AbstractVector{T}) where {T<:Base.IEEEFloat}
```

`x`をホワイトニングされたベクトルに変換します。すなわち、`z = W * (x - μ)`を使用して、変換カーネル`K`を用います。

もし`K`が`n ↦ p`を圧縮する場合、`z ∈ ℝᵖ`です。
