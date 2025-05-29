```
GeneralLinearGroup{𝔽,T}
```

一般線形群 $\mathrm{GL}(n)$ は、すべての可逆行列の集合です

$$
\mathrm{GL}(n) = \bigl\{ M ∈ 𝔽^{n×n}\ \big|\ \mathrm{det}(M) ≠ 0\bigr \},
\qquad 𝔽 ∈ \{ ℝ, ℂ \},
$$

群演算として [`MatrixMultiplicationGroupOperation`](@ref) を備えています。

可逆行列の集合はリーマン多様体であり、行列空間 $ℝ^{n×n}$ の開集合としての埋め込みからその構造を引き継いでいます。

# コンストラクタ

```
GeneralLinearGroup(n::Int; field=ℝ, kwargs...)
```

$$
𝔽^{n×n}
$$

上の一般線形群を生成します。`kwargs...` のすべてのキーワード引数は [`InvertibleMatrices`](@extref `Manifolds.InvertibleMatrices`) に渡されます。
