```
KKTVectorFieldAdjointJacobian{O<:ConstrainedManifoldObjective}
```

KKT条件のベクトル場 $F$ のヤコビアンの随伴を実装します。これは不等式制約のためのスラック変数を含みます。詳細は [`KKTVectorField`](@ref) と [`KKTVectorFieldJacobian`](@ref) を参照してください。

$$
\operatorname{J}^* F(p, μ, λ, s)[X, Y, Z, W] = \begin{pmatrix}
    \operatorname{Hess}_p \mathcal L(p, μ, λ)[X] + \displaystyle\sum_{i=1}^m Y_i \operatorname{grad} g_i(p) + \displaystyle\sum_{j=1}^n Z_j \operatorname{grad} h_j(p)\\
    \Bigl( ⟨\operatorname{grad} g_i(p), X⟩ + s_iW_i\Bigr)_{i=1}^m\\
    \Bigl( ⟨\operatorname{grad} h_j(p), X⟩ \Bigr)_{j=1}^n\\
    μ ⊙ W + Y
\end{pmatrix},
$$

ここで $⊙$ はアダマール（または要素ごとの）積を示します。

また、[`LagrangianHessian`](@ref) $\operatorname{Hess}_p \mathcal L(p, μ, λ)[X]$ も参照してください。

# フィールド

  * `cmo` [`ConstrainedManifoldObjective`](@ref)

# コンストラクタ

```
KKTVectorFieldAdjointJacobian(cmo::ConstrainedManifoldObjective)
```

ある [`ConstrainedManifoldObjective`](@ref) `cmo` に関連するKKTベクトル場の随伴ヤコビアンを生成します。

# 例

ある [`ConstrainedManifoldObjective`](@ref) `cmo` に対して `AdJF = KKTVectorFieldAdjointJacobian(cmo)` を定義し、$N$ を $\mathcal M×ℝ^m×ℝ^n×ℝ^m$ の積多様体とします。次に、このコストを `AdJF(N, q, Y)` またはインプレースバリアント `AdJF(N, Z, q, Y)` として呼び出すことができます。ここで `q` は `N` 上の点であり、`Y` と `Z` は `q` における接ベクトルです。 ```
