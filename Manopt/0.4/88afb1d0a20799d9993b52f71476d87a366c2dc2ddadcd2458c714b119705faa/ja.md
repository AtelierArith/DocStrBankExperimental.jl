```
KKTVectorFieldNormSqGradient{O<:ConstrainedManifoldObjective}
```

[`KKTVectorFieldNormSq`](@ref) $φ(p,μ,λ,s) = \lVert F(p,μ,λ,s)\rVert^2$ の勾配を計算します。これは、[`KKTVectorField`](@ref) $F$ のノルムの二乗です。

これは、[LaiYoshise:2024](@cite) において、彼らのメリット関数の勾配として与えられており、ヤコビアンの随伴 $J^*$ を用いて次のように書くことができます。

$$
\operatorname{grad} φ = 2\operatorname{J}^* F(p, μ, λ, s)[F(p, μ, λ, s)],
$$

したがって、[`KKTVectorFieldAdjointJacobian`](@ref) と [`KKTVectorField`](@ref) を用いて計算されます。

完全性のために、勾配は次のように表されます。最初の成分の省略形として、[`LagrangianGradient`](@ref) $L = \operatorname{grad}_p \mathcal L(p,μ,λ) ∈ T_p\mathcal M$ を使用します。

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

ここで、$⊙$ はハダマール（または要素ごとの）積を示します。

# フィールド

  * `cmo` [`ConstrainedManifoldObjective`](@ref)

# コンストラクタ

```
KKTVectorFieldNormSqGradient(cmo::ConstrainedManifoldObjective)
```

# 例

いくつかの [`ConstrainedManifoldObjective`](@ref) `cmo` に対して `grad_f = KKTVectorFieldNormSqGradient(cmo)` を定義し、$ \mathcal M×ℝ^m×ℝ^n×ℝ^m $ の積多様体を `N` とします。次に、このコストを `grad_f(N, q)` またはインプレースバリアント `grad_f(N, Y, q)` として呼び出すことができます。ここで、`q` は `N` 上の点であり、`Y` は `q` での接ベクトルで、結果として得られる勾配を返します。
