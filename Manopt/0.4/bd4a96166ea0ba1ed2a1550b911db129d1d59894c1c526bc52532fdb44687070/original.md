```
exact_penalty_method(M, F, gradF, p=rand(M); kwargs...)
exact_penalty_method(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
```

perform the exact penalty method (EPM) [LiuBoumal:2019](@cite) The aim of the EPM is to find a solution of the constrained optimisation task

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad  \text{ for } j=1,…,n,
\end{aligned}
$$

where `M` is a Riemannian manifold, and $f$, $\{g_i\}_{i=1}^m$ and $\{h_j\}_{j=1}^n$ are twice continuously differentiable functions from `M` to ℝ. For that a weighted $L_1$-penalty term for the violation of the constraints is added to the objective

$$
f(x) + ρ\biggl( \sum_{i=1}^m \max\bigl\{0, g_i(x)\bigr\} + \sum_{j=1}^n \vert h_j(x)\vert\biggr),
$$

where $ρ>0$ is the penalty parameter. Since this is non-smooth, a [`SmoothingTechnique`](@ref) with parameter `u` is applied, see the [`ExactPenaltyCost`](@ref).

In every step $k$ of the exact penalty method, the smoothed objective is then minimized over all $x ∈\mathcal{M}$. Then, the accuracy tolerance $ϵ$ and the smoothing parameter $u$ are updated by setting

$$
ϵ^{(k)}=\max\{ϵ_{\min}, θ_ϵ ϵ^{(k-1)}\},
$$

where $ϵ_{\min}$ is the lowest value $ϵ$ is allowed to become and $θ_ϵ ∈ (0,1)$ is constant scaling factor, and

$$
u^{(k)} = \max \{u_{\min}, \theta_u u^{(k-1)} \},
$$

where $u_{\min}$ is the lowest value $u$ is allowed to become and $θ_u ∈ (0,1)$ is constant scaling factor.

Finally, the penalty parameter $ρ$ is updated as

$$
ρ^{(k)} = \begin{cases}
ρ^{(k-1)}/θ_ρ,  & \text{if } \displaystyle \max_{j ∈ \mathcal{E},i ∈ \mathcal{I}} \Bigl\{ \vert h_j(x^{(k)}) \vert, g_i(x^{(k)})\Bigr\} \geq u^{(k-1)} \Bigr) ,\\
ρ^{(k-1)}, & \text{else,}
\end{cases}
$$

where $θ_ρ ∈ (0,1)$ is a constant scaling factor.

# Input

  * `M`      a manifold $\mathcal M$
  * `f`      a cost function $f:\mathcal M→ℝ$ to minimize
  * `grad_f` the gradient of the cost function

# Optional (if not called with the [`ConstrainedManifoldObjective`](@ref) `cmo`)

  * `g`:      (`nothing`) the inequality constraints
  * `h`:      (`nothing`) the equality constraints
  * `grad_g`: (`nothing`) the gradient of the inequality constraints
  * `grad_h`: (`nothing`) the gradient of the equality constraints

Note that one of the pairs (`g`, `grad_g`) or (`h`, `grad_h`) has to be provided. Otherwise the problem is not constrained and you should consider using unconstrained solvers like [`quasi_Newton`](@ref).

# Optional

  * `smoothing`:                 ([`LogarithmicSumOfExponentials`](@ref)) [`SmoothingTechnique`](@ref) to use
  * `ϵ`:                         (`1e–3`) the accuracy tolerance
  * `ϵ_exponent`:                (`1/100`) exponent of the ϵ update factor;
  * `ϵ_min`:                     (`1e-6`) the lower bound for the accuracy tolerance
  * `u`:                         (`1e–1`) the smoothing parameter and threshold for violation of the constraints
  * `u_exponent`:                (`1/100`) exponent of the u update factor;
  * `u_min`:                     (`1e-6`) the lower bound for the smoothing parameter and threshold for violation of the constraints
  * `ρ`:                         (`1.0`) the penalty parameter
  * `equality_constraints`:      (`nothing`) the number $n$ of equality constraints.
  * `gradient_range`             (`nothing`, equivalent to [`NestedPowerRepresentation`](@extref) specify how gradients are represented
  * `gradient_equality_range`:   (`gradient_range`) specify how the gradients of the equality constraints are represented
  * `gradient_inequality_range`: (`gradient_range`) specify how the gradients of the inequality constraints are represented
  * `inequality_constraints`:    (`nothing`) the number $m$ of inequality constraints.
  * `min_stepsize`:              (`1e-10`) the minimal step size
  * `sub_cost`:                  ([`ExactPenaltyCost`](@ref)`(problem, ρ, u; smoothing=smoothing)`) use this exact penalty cost, especially with the same numbers `ρ,u` as in the options for the sub problem
  * `sub_grad`:                  ([`ExactPenaltyGrad`](@ref)`(problem, ρ, u; smoothing=smoothing)`) use this exact penalty gradient, especially with the same numbers `ρ,u` as in the options for the sub problem
  * `sub_kwargs`:                (`(;)`) keyword arguments to decorate the sub options, for example debug, that automatically respects the main solvers debug options (like sub-sampling) as well
  * `sub_stopping_criterion`:    ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(ϵ) |`[`StopWhenStepsizeLess`](@ref)`(1e-10)`) specify a stopping criterion for the subsolver.
  * `sub_problem`:               ([`DefaultManoptProblem`](@ref)`(M,`[`ManifoldGradientObjective`](@ref)`(sub_cost, sub_grad; evaluation=evaluation)`, provide a problem for the subsolver
  * `sub_state`:                 ([`QuasiNewtonState`](@ref)) using [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) with [`InverseBFGS`](@ref) and `sub_stopping_criterion` as a stopping criterion. See also `sub_kwargs`.
  * `stopping_criterion`:        ([`StopAfterIteration`](@ref)`(300)` | ([`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min)` & [`StopWhenChangeLess`](@ref)`(1e-10)`) a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.

For the `range`s of the constraints' gradient, other power manifold tangent space representations, mainly the [`ArrayPowerRepresentation`](@extref Manifolds :jl:type:`Manifolds.ArrayPowerRepresentation`) can be used if the gradients can be computed more efficiently in that representation.

With `equality_constraints` and `inequality_constraints` you have to provide the dimension of the ranges of `h` and `g`, respectively. If not provided, together with `M` and the start point `p0`, a call to either of these is performed to try to infer these.

# Output

the obtained (approximate) minimizer $p^*$, see [`get_solver_return`](@ref) for details
