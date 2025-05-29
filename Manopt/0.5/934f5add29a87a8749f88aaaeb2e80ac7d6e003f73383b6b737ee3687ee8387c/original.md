```
exact_penalty_method(M, f, grad_f, p=rand(M); kwargs...)
exact_penalty_method(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
exact_penalty_method!(M, f, grad_f, p; kwargs...)
exact_penalty_method!(M, cmo::ConstrainedManifoldObjective, p; kwargs...)
```

perform the exact penalty method (EPM) [LiuBoumal:2019](@cite) The aim of the EPM is to find a solution of the constrained optimisation task

$$
\begin{aligned}
\operatorname*{arg\,min}_{p ∈ \mathcal M} & f(p)\\
\text{subject to}\quad&g_i(p) ≤ 0 \quad \text{ for } i= 1, …, m,\\
\quad & h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

where `M` is a Riemannian manifold, and $f$, $\{g_i\}_{i=1}^{n}$ and $\{h_j\}_{j=1}^{m}$ are twice continuously differentiable functions from `M` to ℝ. For that a weighted $L_1$-penalty term for the violation of the constraints is added to the objective

$$
f(x) + ρ\biggl( \sum_{i=1}^m \max\bigl\{0, g_i(x)\bigr\} + \sum_{j=1}^n \vert h_j(x)\vert\biggr),
$$

where $ρ>0$ is the penalty parameter.

Since this is non-smooth, a [`SmoothingTechnique`](@ref) with parameter `u` is applied, see the [`ExactPenaltyCost`](@ref).

In every step $k$ of the exact penalty method, the smoothed objective is then minimized over all $p ∈\mathcal M$. Then, the accuracy tolerance $ϵ$ and the smoothing parameter $u$ are updated by setting

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

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `f`: a cost function $f: \mathcal M→ ℝ$ implemented as `(M, p) -> v`
  * `grad_f`: the (Riemannian) gradient $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ of f as a function `(M, p) -> X` or a function `(M, X, p) -> X` computing `X` in-place
  * `p`: a point on the manifold $\mathcal M$

# Keyword arguments

if not called with the [`ConstrainedManifoldObjective`](@ref) `cmo`

  * `g=nothing`: the inequality constraints
  * `h=nothing`: the equality constraints
  * `grad_g=nothing`: the gradient of the inequality constraints
  * `grad_h=nothing`: the gradient of the equality constraints

Note that one of the pairs (`g`, `grad_g`) or (`h`, `grad_h`) has to be provided. Otherwise the problem is not constrained and a better solver would be for example [`quasi_Newton`](@ref).

# Further keyword arguments

  * `ϵ=1e–3`: the accuracy tolerance
  * `ϵ_exponent=1/100`: exponent of the ϵ update factor;
  * `ϵ_min=1e-6`: the lower bound for the accuracy tolerance
  * `u=1e–1`: the smoothing parameter and threshold for violation of the constraints
  * `u_exponent=1/100`: exponent of the u update factor;
  * `u_min=1e-6`: the lower bound for the smoothing parameter and threshold for violation of the constraints
  * `ρ=1.0`: the penalty parameter
  * `equality_constraints=nothing`: the number $n$ of equality constraints. If not provided, a call to the gradient of `g` is performed to estimate these.
  * `gradient_range=nothing`: specify how both gradients of the constraints are represented
  * `gradient_equality_range=gradient_range`:  specify how gradients of the equality constraints are represented, see [`VectorGradientFunction`](@ref).
  * `gradient_inequality_range=gradient_range`:  specify how gradients of the inequality constraints are represented, see [`VectorGradientFunction`](@ref).
  * `inequality_constraints=nothing`: the number $m$ of inequality constraints.  If not provided, a call to the gradient of `g` is performed to estimate these.
  * `min_stepsize=1e-10`: the minimal step size
  * `smoothing=`[`LogarithmicSumOfExponentials`](@ref): a [`SmoothingTechnique`](@ref) to use
  * `sub_cost=`[`ExactPenaltyCost`](@ref)`(problem, ρ, u; smoothing=smoothing)`: cost to use in the sub solver This is used to define the `sub_problem=` keyword and has hence no effect, if you set `sub_problem` directly.
  * `sub_grad=`[`ExactPenaltyGrad`](@ref)`(problem, ρ, u; smoothing=smoothing)`: gradient to use in the sub solver This is used to define the `sub_problem=` keyword and has hence no effect, if you set `sub_problem` directly.
  * `sub_kwargs=``(;)`: a named tuple of keyword arguments that are passed to [`decorate_objective!`](@ref) of the sub solvers objective, the [`decorate_state!`](@ref) of the subsovlers state, and the sub state constructor itself.
  * `sub_stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(ϵ)`[`|`](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-10)`: a stopping cirterion for the sub solver This is used to define the `sub_state=` keyword and has hence no effect, if you set `sub_state` directly.
  * `sub_state=`[`DefaultManoptProblem`](@ref)`(M,`[`ManifoldGradientObjective`](@ref)`(sub*cost, sub*grad; evaluation=evaluation):  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `sub_state=`[`QuasiNewtonState`](@ref):  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function. where [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) with [`InverseBFGS`](@ref) is used
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)`(`[`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min)`[`&`](@ref StopWhenAll)[`StopWhenChangeLess`](@ref)`(1e-10) )`: a functor indicating that the stopping criterion is fulfilled

For the `range`s of the constraints' gradient, other power manifold tangent space representations, mainly the [`ArrayPowerRepresentation`](@extref Manifolds :jl:type:`Manifolds.ArrayPowerRepresentation`) can be used if the gradients can be computed more efficiently in that representation.

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective decorators, respectively.

# Output

The obtained approximate minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
