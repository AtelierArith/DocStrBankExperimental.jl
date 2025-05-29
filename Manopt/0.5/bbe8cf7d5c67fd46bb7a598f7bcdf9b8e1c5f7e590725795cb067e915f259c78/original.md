```
augmented_Lagrangian_method(M, f, grad_f, p=rand(M); kwargs...)
augmented_Lagrangian_method(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
augmented_Lagrangian_method!(M, f, grad_f, p; kwargs...)
augmented_Lagrangian_method!(M, cmo::ConstrainedManifoldObjective, p; kwargs...)
```

perform the augmented Lagrangian method (ALM) [LiuBoumal:2019](@cite). This method can work in-place of `p`.

The aim of the ALM is to find the solution of the constrained optimisation task

$$
\begin{aligned}
\operatorname*{arg\,min}_{p ∈ \mathcal M} & f(p)\\
\text{subject to}\quad&g_i(p) ≤ 0 \quad \text{ for } i= 1, …, m,\\
\quad & h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

where `M` is a Riemannian manifold, and $f$, $\{g_i\}_{i=1}^{n}$ and $\{h_j\}_{j=1}^{m}$ are twice continuously differentiable functions from `M` to ℝ. In every step $k$ of the algorithm, the [`AugmentedLagrangianCost`](@ref)  $\mathcal L_{ρ^{(k)}}(p, μ^{(k)}, λ^{(k)})$ is minimized on \mathcal M,   where $μ^{(k)} ∈ ℝ^n$ and $λ^{(k)} ∈ ℝ^m$ are the current iterates of the Lagrange multipliers and $ρ^{(k)}$ is the current penalty parameter.

The Lagrange multipliers are then updated by

$$
λ_j^{(k+1)} =\operatorname{clip}_{[λ_{\min},λ_{\max}]} (λ_j^{(k)} + ρ^{(k)} h_j(p^{(k+1)})) \text{for all} j=1,…,p,
$$

and

$$
μ_i^{(k+1)} =\operatorname{clip}_{[0,μ_{\max}]} (μ_i^{(k)} + ρ^{(k)} g_i(p^{(k+1)})) \text{ for all } i=1,…,m,
$$

where $λ_{\text{min}} ≤ λ_{\text{max}}$ and $μ_{\text{max}}$ are the multiplier boundaries.

Next, the accuracy tolerance $ϵ$ is updated as

$$
ϵ^{(k)}=\max\{ϵ_{\min}, θ_ϵ ϵ^{(k-1)}\},
$$

where $ϵ_{\text{min}}$ is the lowest value $ϵ$ is allowed to become and $θ_ϵ ∈ (0,1)$ is constant scaling factor.

Last, the penalty parameter $ρ$ is updated as follows: with

$$
σ^{(k)}=\max_{j=1,…,p, i=1,…,m} \{\|h_j(p^{(k)})\|, \|\max_{i=1,…,m}\{g_i(p^{(k)}), -\frac{μ_i^{(k-1)}}{ρ^{(k-1)}} \}\| \}.
$$

`ρ` is updated as

$$
ρ^{(k)} = \begin{cases}
ρ^{(k-1)}/θ_ρ,  & \text{if } σ^{(k)}\leq θ_ρ σ^{(k-1)} ,\\
ρ^{(k-1)}, & \text{else,}
\end{cases}
$$

where $θ_ρ ∈ (0,1)$ is a constant scaling factor.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place

# Optional (if not called with the [`ConstrainedManifoldObjective`](@ref) `cmo`)

  * `g=nothing`: the inequality constraints
  * `h=nothing`: the equality constraints
  * `grad_g=nothing`: the gradient of the inequality constraints
  * `grad_h=nothing`: the gradient of the equality constraints

Note that one of the pairs (`g`, `grad_g`) or (`h`, `grad_h`) has to be provided. Otherwise the problem is not constrained and a better solver would be for example [`quasi_Newton`](@ref).

# Keyword Arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `ϵ=1e-3`:           the accuracy tolerance
  * `ϵ_min=1e-6`:       the lower bound for the accuracy tolerance
  * `ϵ_exponent=1/100`: exponent of the ϵ update factor; also 1/number of iterations until maximal accuracy is needed to end algorithm naturally

      * `equality_constraints=nothing`: the number $n$ of equality constraints.

    If not provided, a call to the gradient of `g` is performed to estimate these.
  * `gradient_range=nothing`: specify how both gradients of the constraints are represented
  * `gradient_equality_range=gradient_range`:  specify how gradients of the equality constraints are represented, see [`VectorGradientFunction`](@ref).
  * `gradient_inequality_range=gradient_range`:  specify how gradients of the inequality constraints are represented, see [`VectorGradientFunction`](@ref).
  * `inequality_constraints=nothing`: the number $m$ of inequality constraints.  If not provided, a call to the gradient of `g` is performed to estimate these.
  * `λ=ones(size(h(M,x),1))`: the Lagrange multiplier with respect to the equality constraints
  * `λ_max=20.0`:       an upper bound for the Lagrange multiplier belonging to the equality constraints
  * `λ_min=- λ_max`:    a lower bound for the Lagrange multiplier belonging to the equality constraints
  * `μ=ones(size(h(M,x),1))`: the Lagrange multiplier with respect to the inequality constraints
  * `μ_max=20.0`: an upper bound for the Lagrange multiplier belonging to the inequality constraints
  * `ρ=1.0`:            the penalty parameter
  * `τ=0.8`:            factor for the improvement of the evaluation of the penalty parameter
  * `θ_ρ=0.3`:          the scaling factor of the penalty parameter
  * `θ_ϵ=(ϵ_min / ϵ)^(ϵ_exponent)`: the scaling factor of the exactness
  * `sub_cost=[`AugmentedLagrangianCost± (@ref)`(cmo, ρ, μ, λ):` use augmented Lagrangian cost, based on the [`ConstrainedManifoldObjective`](@ref) build from the functions provided.  This is used to define the `sub_problem=` keyword and has hence no effect, if you set `sub_problem` directly.
  * `sub_grad=[`AugmentedLagrangianGrad`](@ref)`(cmo, ρ, μ, λ)`: use augmented Lagrangian gradient, based on the [`ConstrainedManifoldObjective`](@ref) build from the functions provided. This is used to define the`sub*problem=`keyword and has hence no effect, if you set`sub*problem` directly.
  * `sub_kwargs=``(;)`: a named tuple of keyword arguments that are passed to [`decorate_objective!`](@ref) of the sub solvers objective, the [`decorate_state!`](@ref) of the subsovlers state, and the sub state constructor itself.
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)([`StopWhenSmallerOrEqual`](@ref)`(:ϵ, ϵ_min)`[`&`](@ref StopWhenAll)[`StopWhenChangeLess`](@ref)`(1e-10) )`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`: a functor indicating that the stopping criterion is fulfilled
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state=`[`QuasiNewtonState`](@ref):  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.as the quasi newton method, the [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) with [`InverseBFGS`](@ref) is used.
  * `sub_stopping_criterion::StoppingCriterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(ϵ)`[`|`](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-8)`,

For the `range`s of the constraints' gradient, other power manifold tangent space representations, mainly the [`ArrayPowerRepresentation`](@extref Manifolds :jl:type:`Manifolds.ArrayPowerRepresentation`) can be used if the gradients can be computed more efficiently in that representation.

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
