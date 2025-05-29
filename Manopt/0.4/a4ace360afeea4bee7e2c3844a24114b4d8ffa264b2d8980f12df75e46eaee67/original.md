```
CondensedKKTVectorFieldJacobian{O<:ConstrainedManifoldObjective,T,R}  <: AbstractConstrainedSlackFunctor{T,R}
```

Given the constrained optimization problem

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

we reformulate the KKT conditions of the Lagrangian from the optimality conditions of the Lagrangian

$$
\mathcal L(p, μ, λ) = f(p) + \sum_{j=1}^n λ_jh_j(p) + \sum_{i=1}^m μ_ig_i(p)
$$

in a perturbed / barrier method enhanced as well as condensed form as using $\operatorname{grad}_o L(p, μ, λ)$ the Riemannian gradient of the Lagrangian with respect to the first parameter.

Let $\mathcal N = \mathcal M × ℝ^n$. We obtain the linear system

$$
\mathcal A(p,λ)[X,Y] = -b(p,λ),\qquad \text{where } X ∈ T_p\mathcal M, Y ∈ ℝ^n
$$

where $\mathcal A: T_{(p,λ)}\mathcal N → T_{(p,λ)}\mathcal N$ is a linear operator on $T_{(p,λ)}\mathcal N = T_p\mathcal M × ℝ^n$ given by

$$
\mathcal A(p,λ)[X,Y] = \begin{pmatrix}
\operatorname{Hess}_p\mathcal L(p, μ, λ)[X]
+ \displaystyle\sum_{i=1}^m \frac{μ_i}{s_i}⟨\operatorname{grad} g_i(p), X⟩\operatorname{grad} g_i(p)
+ \displaystyle\sum_{j=1}^n Y_j \operatorname{grad} h_j(p)
\\
\Bigl( ⟨\operatorname{grad} h_j(p), X⟩ \Bigr)_{j=1}^n
\end{pmatrix}
$$

# Fields

  * `cmo` the [`ConstrainedManifoldObjective`](@ref)
  * `μ::V` the vector in $ℝ^m$ of coefficients for the inequality constraints
  * `s::V` the vector in $ℝ^m$ of slack variables
  * `β::R` the barrier parameter $β∈ℝ$

# Constructor

```
CondensedKKTVectorFieldJacobian(cmo, μ, s, β)
```
