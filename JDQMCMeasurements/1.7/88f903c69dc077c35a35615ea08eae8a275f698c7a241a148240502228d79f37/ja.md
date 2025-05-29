```
susceptibility(S::AbstractVector{T}, Δτ::E) where {T<:Number, E<:AbstractFloat}
```

感受性を計算します

$$
\chi = \int_0^\beta S(\tau) d\tau,
$$

ここで、相関データは `S` に格納されています。積分は、ステップサイズ `Δτ` を使用してシンプソン法で行われます。
