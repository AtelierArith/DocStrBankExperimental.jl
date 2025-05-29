```
susceptibility!(χ::AbstractArray{T}, S::AbstractArray{T}, Δτ::E, dim::Int) where {T<:Number, E<:AbstractFloat}
```

感受率を計算します

$$
\chi_\mathbf{n} = \int_0^\beta S_\mathbf{n}(\tau) d\tau,
$$

ここで、$\chi_\mathbf{n}$ 感受率は `χ` に書き込まれ、`S` には統合する必要がある $S_\mathbf{n}(\tau)$ 相関が含まれています。パラメータ `Δτ` は虚時間 $\tau$ における離散化であり、虚時間にわたる積分を数値的に評価するためにシンプソン法で使用されるステップサイズです。引数 `dim` は、`S` のどの次元が虚時間に対応するかを指定し、統合する必要があります。したがって、

```julia
ndim(χ)+1 == ndim(S)
```

および

```julia
size(χ) == size(selectdim(S, dim, 1))
```

の両方が真でなければなりません。
