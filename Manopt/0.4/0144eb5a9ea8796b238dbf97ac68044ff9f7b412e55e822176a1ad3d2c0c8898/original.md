```
augmented_Lagrangian_method(M, f, grad_f, p=rand(M); kwargs...)
augmented_Lagrangian_method(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
```

perform the augmented Lagrangian method (ALM) [LiuBoumal:2019](@cite).

The aim of the ALM is to find the solution of the constrained optimisation task

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

where `M` is a Riemannian manifold, and $f$, $\{g_i\}_{i=1}^m$ and $\{h_j\}_{j=1}^p$ are twice continuously differentiable functions from `M` to ℝ. In every step $k$ of the algorithm, the [`AugmentedLagrangianCost`](@ref) $\mathcal{L}_{ρ^{(k-1)}}(p, μ^{(k-1)}, λ^{(k-1)})$ is minimized on $\mathcal{M}$, where $μ^{(k-1)} ∈ \mathbb R^n$ and $λ^{(k-1)} ∈ ℝ^m$ are the current iterates of the Lagrange multipliers and $ρ^{(k-1)}$ is the current penalty parameter.

The Lagrange multipliers are then updated by

$$
λ_j^{(k)} =\operatorname{clip}_{[λ_{\min},λ_{\max}]} (λ_j^{(k-1)} + ρ^{(k-1)} h_j(p^{(k)})) \text{for all} j=1,…,p,
$$

and

$$
μ_i^{(k)} =\operatorname{clip}_{[0,μ_{\max}]} (μ_i^{(k-1)} + ρ^{(k-1)} g_i(p^{(k)})) \text{ for all } i=1,…,m,
$$

where $λ_{\min} \leq λ_{\max}$ and $μ_{\max}$ are the multiplier boundaries.

Next, the accuracy tolerance $ϵ$ is updated as

$$
ϵ^{(k)}=\max\{ϵ_{\min}, θ_ϵ ϵ^{(k-1)}\},
$$

where $ϵ_{\min}$ is the lowest value $ϵ$ is allowed to become and $θ_ϵ ∈ (0,1)$ is constant scaling factor.

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

  * `M`      a manifold $\mathcal M$
  * `f`      a cost function $F:\mathcal M→ℝ$ to minimize
  * `grad_f` the gradient of the cost function

# Optional (if not called with the [`ConstrainedManifoldObjective`](@ref) `cmo`)

  * `g`:      (`nothing`) the inequality constraints
  * `h`:      (`nothing`) the equality constraints
  * `grad_g`: (`nothing`) the gradient of the inequality constraints
  * `grad_h`: (`nothing`) the gradient of the equality constraints

Note that one of the pairs (`g`, `grad_g`) or (`h`, `grad_h`) has to be provided. Otherwise the problem is not constrained and a better solver would be for example [`quasi_Newton`](@ref).

# Optional

  * `ϵ`:                         (`1e-3`) the accuracy tolerance
  * `ϵ_min`:                     (`1e-6`) the lower bound for the accuracy tolerance
  * `ϵ_exponent`:                (`1/100`) exponent of the ϵ update factor;  also 1/number of iterations until maximal accuracy is needed to end algorithm naturally
  * `θ_ϵ`:                       (`(ϵ_min / ϵ)^(ϵ_exponent)`) the scaling factor of the exactness
  * `μ`:                         (`ones(size(h(M,x),1))`) the Lagrange multiplier with respect to the inequality constraints
  * `μ_max`:                     (`20.0`) an upper bound for the Lagrange multiplier belonging to the inequality constraints
  * `λ`:                         (`ones(size(h(M,x),1))`) the Lagrange multiplier with respect to the equality constraints
  * `λ_max`:                     (`20.0`) an upper bound for the Lagrange multiplier belonging to the equality constraints
  * `λ_min`:                     (`- λ_max`) a lower bound for the Lagrange multiplier belonging to the equality constraints
  * `τ`:                         (`0.8`) factor for the improvement of the evaluation of the penalty parameter
  * `ρ`:                         (`1.0`) the penalty parameter
  * `θ_ρ`:                       (`0.3`) the scaling factor of the penalty parameter
  * `equality_constraints`:      (`nothing`) the number $n$ of equality constraints.
  * `gradient_range`             (`nothing`, equivalent to [`NestedPowerRepresentation`](@extref) specify how gradients are represented
  * `gradient_equality_range`:   (`gradient_range`) specify how the gradients of the equality constraints are represented
  * `gradient_inequality_range`: (`gradient_range`) specify how the gradients of the inequality constraints are represented
  * `inequality_constraints`:    (`nothing`) the number $m$ of inequality constraints.
  * `sub_grad`:                  ([`AugmentedLagrangianGrad`](@ref)`(problem, ρ, μ, λ)`) use augmented Lagrangian gradient, especially with the same numbers `ρ,μ` as in the options for the sub problem
  * `sub_kwargs`:                (`(;)`) keyword arguments to decorate the sub options, for example the `debug=` keyword.
  * `sub_stopping_criterion`:    ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(ϵ) |`[`StopWhenStepsizeLess`](@ref)`(1e-8)`) specify a stopping criterion for the subsolver.
  * `sub_problem`:               ([`DefaultManoptProblem`](@ref)`(M,`[`ConstrainedManifoldObjective`](@ref)`(subcost, subgrad; evaluation=evaluation))`) problem for the subsolver
  * `sub_state`:                 ([`QuasiNewtonState`](@ref)) using [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) with [`InverseBFGS`](@ref) and `sub_stopping_criterion` as a stopping criterion. See also `sub_kwargs`.
  * `stopping_criterion`:        ([`StopAfterIteration`](@ref)`(300)` | ([`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min)` & [`StopWhenChangeLess`](@ref)`(1e-10))`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.

For the `range`s of the constraints' gradient, other power manifold tangent space representations, mainly the [`ArrayPowerRepresentation`](@extref Manifolds :jl:type:`Manifolds.ArrayPowerRepresentation`) can be used if the gradients can be computed more efficiently in that representation.

With `equality_constraints` and `inequality_constraints` you have to provide the dimension of the ranges of `h` and `g`, respectively. If not provided, together with `M` and the start point `p0`, a call to either of these is performed to try to infer these.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
