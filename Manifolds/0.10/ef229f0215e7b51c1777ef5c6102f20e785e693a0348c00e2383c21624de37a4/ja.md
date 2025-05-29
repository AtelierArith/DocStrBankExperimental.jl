```
convert(::Type{PoincareBallPoint}, p::HyperboloidPoint)
convert(::Type{PoincareBallPoint}, p::T) where {T<:AbstractVector}
```

[`HyperboloidPoint`](@ref) $p∈ℝ^{n+1}$ を [`Hyperbolic`](@ref) 多様体 $\mathcal H^n$ のハイパーボロイドモデルから、[`PoincareBallPoint`](@ref) $π(p)∈ℝ^{n}$ に変換します。これはポアンカレボールモデルにおける変換です。等距変換は次のように定義されます。

$$
π(p) = \frac{1}{1+p_{n+1}} \begin{pmatrix}p_1\\⋮\\p_n\end{pmatrix}
$$

これは `x` がベクトルのときにも使用されることに注意してください。
