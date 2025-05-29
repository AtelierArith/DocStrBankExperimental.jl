```
CondensedKKTVectorField{O<:ConstrainedManifoldObjective,T,R} <: AbstractConstrainedSlackFunctor{T,R}
```

Given the constrained optimization problem

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

Then reformulating the KKT conditions of the Lagrangian from the optimality conditions of the Lagrangian

$$
\mathcal L(p, μ, λ) = f(p) + \sum_{j=1}^n λ_jh_j(p) + \sum_{i=1}^m μ_ig_i(p)
$$

in a perturbed / barrier method in a condensed form using a slack variable $s ∈ ℝ^m$ and a barrier parameter $β$ and the Riemannian gradient of the Lagrangian with respect to the first parameter $\operatorname{grad}_p L(p, μ, λ)$.

Let $\mathcal N = \mathcal M × ℝ^n$. We obtain the linear system

$$
\mathcal A(p,λ)[X,Y] = -b(p,λ),\qquad \text{where } (X,Y) ∈ T_{(p,λ)}\mathcal N
$$

where $\mathcal A: T_{(p,λ)}\mathcal N → T_{(p,λ)}\mathcal N$ is a linear operator and this struct models the right hand side $b(p,λ) ∈ T_{(p,λ)}\mathcal M$ given by

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

# Fields

  * `cmo` the [`ConstrainedManifoldObjective`](@ref)
  * `μ::T` the vector in $ℝ^m$ of coefficients for the inequality constraints
  * `s::T` the vector in $ℝ^m$ of sclack variables
  * `β::R` the barrier parameter $β∈ℝ$

# Constructor

```
CondensedKKTVectorField(cmo, μ, s, β)
```
