```
KKTVectorFieldJacobian{O<:ConstrainedManifoldObjective}
```

KKT条件のベクトル場$F$のヤコビアンを実装します。これは、不等式制約のためのスラック変数を含みます。詳細は[`KKTVectorField`](@ref)および[`KKTVectorFieldAdjointJacobian`](@ref)を参照してください。

$$
\operatorname{J} F(p, μ, λ, s)[X, Y, Z, W] = \begin{pmatrix}
    \operatorname{Hess}_p \mathcal L(p, μ, λ)[X] + \displaystyle\sum_{i=1}^m Y_i \operatorname{grad} g_i(p) + \displaystyle\sum_{j=1}^n Z_j \operatorname{grad} h_j(p)\\
    \Bigl( ⟨\operatorname{grad} g_i(p), X⟩ + W_i\Bigr)_{i=1}^m\\
    \Bigl( ⟨\operatorname{grad} h_j(p), X⟩ \Bigr)_{j=1}^n\\
    μ ⊙ W + s ⊙ Y
\end{pmatrix},
$$

ここで、$⊙$はハダマール（または要素ごとの）積を示します。

また、[`LagrangianHessian`](@ref) $\operatorname{Hess}_p \mathcal L(p, μ, λ)[X]$も参照してください。

# フィールド

  * `cmo` [`ConstrainedManifoldObjective`](@ref)

# コンストラクタ

```
KKTVectorFieldJacobian(cmo::ConstrainedManifoldObjective)
```

ある[`ConstrainedManifoldObjective`](@ref) `cmo`に関連するKKTベクトル場のヤコビアンを生成します。

# 例

ある[`ConstrainedManifoldObjective`](@ref) `cmo`に対して`JF = KKTVectorFieldJacobian(cmo)`を定義し、$N$を$\mathcal M×ℝ^m×ℝ^n×ℝ^m$の積多様体とします。次に、このコストを`JF(N, q, Y)`またはインプレースバリアント`JF(N, Z, q, Y)`として呼び出すことができます。ここで、`q`は$N$上の点であり、`Y`と`Z`は$q$での接ベクトルです。
