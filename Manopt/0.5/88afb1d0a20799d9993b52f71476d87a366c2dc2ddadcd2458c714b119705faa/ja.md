```
KKTVectorFieldNormSqGradient{O<:ConstrainedManifoldObjective}
```

[`KKTVectorFieldNormSq`](@ref) $φ(p,μ,λ,s) = \lVert F(p,μ,λ,s)\rVert^2$ の勾配を計算します。これは、[`KKTVectorField`](@ref) $F$ のノルムの二乗です。

これは、[LaiYoshise:2024](@cite) において、彼らのメリット関数の勾配として与えられており、ヤコビアンの随伴 $J^*$ を用いて次のように書くことができます。

$$
\operatorname{grad} φ = 2\operatorname{J}^* F(p, μ, λ, s)[F(p, μ, λ, s)],
$$

したがって、[`KKTVectorFieldAdjointJacobian`](@ref) と [`KKTVectorField`](@ref) を用いて計算されます。

完全性のために、勾配は、[`LagrangianGradient`](@ref) $L = \operatorname{grad}_p \mathcal L(p,μ,λ) ∈ T_p\mathcal M$ を用いて、$F$ の最初の成分の省略形として次のように表されます。

$$
\operatorname{grad} φ
=
2 \begin{pmatrix}
\operatorname{grad}_p \mathcal L(p,μ,λ)[L] + (g_i(p) + s_i)\operatorname{grad} g_i(p) + h_j(p)\operatorname{grad} h_j(p)\\
  \Bigl( ⟨\operatorname{grad} g_i(p), L⟩ + s_i\Bigr)_{i=1}^m + μ ⊙ s ⊙ s\\
  \Bigl( ⟨\operatorname{grad} h_j(p), L⟩ \Bigr)_{j=1}^n\\
  g + s + μ ⊙ μ ⊙ s
\end{pmatrix},
$$

ここで、$⊙$ はアダマール（または要素ごとの）積を示します。

# フィールド

  * `cmo` [`ConstrainedManifoldObjective`](@ref)

# コンストラクタ

```
KKTVectorFieldNormSqGradient(cmo::ConstrainedManifoldObjective)
```

# 例

いくつかの [`ConstrainedManifoldObjective`](@ref) `cmo` に対して `grad_f = KKTVectorFieldNormSqGradient(cmo)` を定義し、$N$ を $\mathcal M×ℝ^m×ℝ^n×ℝ^m$ の積多様体とします。次に、このコストを `grad_f(N, q)` またはインプレースバリアント `grad_f(N, Y, q)` として呼び出すことができ、ここで `q` は `N` 上の点であり、`Y` は `q` での接ベクトルで、結果として得られる勾配を返します。 ```
