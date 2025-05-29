```
CondensedKKTVectorField{O<:ConstrainedManifoldObjective,T,R} <: AbstractConstrainedSlackFunctor{T,R}
```

与えられた制約付き最適化問題

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

次に、ラグランジアンの最適性条件からラグランジアンのKKT条件を再定式化します。

$$
\mathcal L(p, μ, λ) = f(p) + \sum_{j=1}^n λ_jh_j(p) + \sum_{i=1}^m μ_ig_i(p)
$$

スラック変数 $s ∈ ℝ^m$ とバリアパラメータ $β$ を使用して、摂動/バリア法で圧縮された形式でラグランジアンのリーマン勾配に関して最初のパラメータ $\operatorname{grad}_p L(p, μ, λ)$ を用います。

$$
\mathcal N = \mathcal M × ℝ^n
$$

とします。線形系を得ます。

$$
\mathcal A(p,λ)[X,Y] = -b(p,λ),\qquad \text{where } (X,Y) ∈ T_{(p,λ)}\mathcal N
$$

ここで、$\mathcal A: T_{(p,λ)}\mathcal N → T_{(p,λ)}\mathcal N$ は線形演算子であり、この構造は右辺 $b(p,λ) ∈ T_{(p,λ)}\mathcal M$ をモデル化します。

$$
b(p,λ) = \begin{pmatrix}
\operatorname{grad} f(p)
+ \displaystyle\sum_{j=1}^n λ_j \operatorname{grad} h_j(p)
+ \displaystyle\sum_{i=1}^m μ_i \operatorname{grad} g_i(p)
+ \displaystyle\sum_{i=1}^m \frac{μ_i}{s_i}\bigl(
  μ_i(g_i(p)+s_i) + β - μ_is_i
\bigr)\operatorname{grad} g_i(p)\\
h(p)
\end{pmatrix}
$$

# フィールド

  * `cmo` the [`ConstrainedManifoldObjective`](@ref)
  * `μ::T` 不等式制約の係数のベクトル $ℝ^m$ の
  * `s::T` スラック変数のベクトル $ℝ^m$ の
  * `β::R` バリアパラメータ $β∈ℝ$

# コンストラクタ

```
CondensedKKTVectorField(cmo, μ, s, β)
```
