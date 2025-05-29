```
CondensedKKTVectorFieldJacobian{O<:ConstrainedManifoldObjective,T,R}  <: AbstractConstrainedSlackFunctor{T,R}
```

与えられた制約付き最適化問題

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

に対して、ラグランジアンの最適性条件からラグランジアンのKKT条件を再定式化します。

$$
\mathcal L(p, μ, λ) = f(p) + \sum_{j=1}^n λ_jh_j(p) + \sum_{i=1}^m μ_ig_i(p)
$$

摂動/バリア法を強化した凝縮形式で、最初のパラメータに関するラグランジアンのリーマン勾配 $\operatorname{grad}_o L(p, μ, λ)$ を使用します。

$$
\mathcal N = \mathcal M × ℝ^n
$$

とします。線形系を得ます。

$$
\mathcal A(p,λ)[X,Y] = -b(p,λ),\qquad \text{where } X ∈ T_p\mathcal M, Y ∈ ℝ^n
$$

ここで、$\mathcal A: T_{(p,λ)}\mathcal N → T_{(p,λ)}\mathcal N$ は $T_{(p,λ)}\mathcal N = T_p\mathcal M × ℝ^n$ 上の線形演算子であり、次のように与えられます。

$$
\mathcal A(p,λ)[X,Y] = \begin{pmatrix}
\operatorname{Hess}_p\mathcal L(p, μ, λ)[X]
+ \displaystyle\sum_{i=1}^m \frac{μ_i}{s_i}⟨\operatorname{grad} g_i(p), X⟩\operatorname{grad} g_i(p)
+ \displaystyle\sum_{j=1}^n Y_j \operatorname{grad} h_j(p)
\\
\Bigl( ⟨\operatorname{grad} h_j(p), X⟩ \Bigr)_{j=1}^n
\end{pmatrix}
$$

# フィールド

  * `cmo` the [`ConstrainedManifoldObjective`](@ref)
  * `μ::V` 不等式制約の係数のベクトル $ℝ^m$ の中の
  * `s::V` スラック変数のベクトル $ℝ^m$ の中の
  * `β::R` バリアパラメータ $β∈ℝ$

# コンストラクタ

```
CondensedKKTVectorFieldJacobian(cmo, μ, s, β)
```
