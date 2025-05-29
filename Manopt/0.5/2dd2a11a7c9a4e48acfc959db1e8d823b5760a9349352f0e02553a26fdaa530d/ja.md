```
KKTVectorField{O<:ConstrainedManifoldObjective}
```

不等式制約のためのスラック変数を含むベクトル場 $F$ KKT条件を実装します。

[`LagrangianCost`](@ref) に基づいて

$$
\mathcal L(p; μ, λ) = f(p) + \sum_{i=1}^m μ_ig_i(p) + \sum_{j=1}^n λ_jh_j(p)
$$

[`LagrangianGradient`](@ref) に基づいて

$$
\operatorname{grad}\mathcal L(p, μ, λ) = \operatorname{grad}f(p) + \sum_{j=1}^n λ_j \operatorname{grad} h_j(p) + \sum_{i=1}^m μ_i \operatorname{grad} g_i(p),
$$

およびスラック変数 $s=-g(p) ∈ ℝ^m$ を導入すると、ベクトル場は次のように与えられます。

$$
F(p, μ, λ, s) = \begin{pmatrix}
\operatorname{grad}_p \mathcal L(p, μ, λ)\\
g(p) + s\\
h(p)\\
μ ⊙ s
\end{pmatrix}, \text{ ここで } p \in \mathcal M, μ, s \in ℝ^m\text{ および } λ \in ℝ^n,
$$

ここで $⊙$ はハダマール（または要素ごとの）積を示します。

# フィールド

  * `cmo` [`ConstrainedManifoldObjective`](@ref)

点 `p` は任意で通常は必要ありませんが、計算の内部メモリとして機能します。さらに、両方のフィールドは、使用するための積多様体構造を明確にします。

# コンストラクタ

```
KKTVectorField(cmo::ConstrainedManifoldObjective)
```

# 例

いくつかの [`ConstrainedManifoldObjective`](@ref) `cmo` に対して `F = KKTVectorField(cmo)` を定義し、$N$ を $\mathcal M×ℝ^m×ℝ^n×ℝ^m$ の積多様体とします。次に、このコストを `F(N, q)` またはインプレースバリアント `F(N, Y, q)` として呼び出すことができます。ここで `q` は `N` 上の点であり、`Y` は結果のための `q` における接ベクトルです。
