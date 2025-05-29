```
convert(::Type{PoincareBallTangentVector}, p::HyperboloidPoint, X::HyperboloidTangentVector)
convert(::Type{PoincareBallTangentVector}, p::P, X::T) where {P<:AbstractVector, T<:AbstractVector}
```

[`HyperboloidTangentVector`](@ref) `X`を点`p`で[`PoincareBallTangentVector`](@ref)に変換するには、ハイパーボロイドからポアンカレボールへの等長写像$π$のプッシュフォワード$π_*(p)[X]$を計算します。これは[`convert(::Type{PoincareBallPoint}, ::HyperboloidPoint)`](@ref)を参照してください。

式は次のようになります。

$$
π_*(p)[X] = \frac{1}{p_{n+1}+1}\Bigl(\tilde X - \frac{X_{n+1}}{p_{n+1}+1}\tilde p \Bigl),
$$

ここで、$\tilde X = \begin{pmatrix}X_1\\⋮\\X_n\end{pmatrix}$および$\tilde p = \begin{pmatrix}p_1\\⋮\\p_n\end{pmatrix}$です。
