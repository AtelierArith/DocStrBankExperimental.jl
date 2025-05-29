```
SpecialLinear{𝔽,T}
```

特別線形群 $\mathrm{SL}(n,𝔽)$ は、$𝔽^{n×n}$ における単位行列式を持つすべての可逆行列の群であり、群演算として [`MatrixMultiplicationGroupOperation`](@ref) を持ちます。

リー代数 $\mathfrak sl(n, 𝔽) = T_e \mathrm{SL}(n,𝔽)$ は、トレースがゼロのすべての行列の集合です。デフォルトでは、$p ∈ \mathrm{SL}(n,𝔽)$ に対する接ベクトル $X_p ∈ T_p \mathrm{SL}(n,𝔽)$ は、対応するリー代数ベクトル $X_e = p^{-1}X_p ∈ 𝔰𝔩(n, 𝔽)$ で表されます。

# コンストラクタ

```
GeneralLinearGroup(n::Int, field=ℝ; kwargs...)
```

$$
𝔽^{n×n}
$$

上の一般線形群を生成します。`kwargs...` のすべてのキーワード引数は、[`DeterminantOneMatrices`](@extref `Manifolds.DeterminantOneMatrices`) に渡されます。
