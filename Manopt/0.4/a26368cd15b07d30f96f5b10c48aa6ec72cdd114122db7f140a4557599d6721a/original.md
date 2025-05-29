```
interior_point_Newton(M, f, grad_f, Hess_f, p=rand(M); kwargs...)
interior_point_Newton(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
interior_point_Newton!(M, f, grad_f, Hess_f, p; kwargs...)
interior_point_Newton(M, ConstrainedManifoldObjective, p; kwargs...)
```

perform the interior point Newton method following [LaiYoshise:2024](@cite).

In order to solve the constrained problem

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

This algorithms iteratively solves the linear system based on extending the KKT system by a slack variable `s`.

$$
\operatorname{J} F(p, μ, λ, s)[X, Y, Z, W] = -F(p, μ, λ, s),
\text{ where }
X ∈ T_p\mathcal M, Y,W ∈ ℝ^m, Z ∈ ℝ^n,
$$

see [`CondensedKKTVectorFieldJacobian`](@ref) and [`CondensedKKTVectorField`](@ref), respectively, for the reduced form, this is usually solved in. From the resulting `X` and `Z` in the reeuced form, the other two, $Y$, $W$, are then computed.

From the gradient $(X,Y,Z,W)$ at the current iterate $(p, μ, λ, s)$, a line search is performed using the [`KKTVectorFieldNormSq`](@ref) norm of the KKT vector field (squared) and its gradient [`KKTVectorFieldNormSqGradient`](@ref) together with the [`InteriorPointCentralityCondition`](@ref).

Note that since the vector field $F$ includes the gradients of the constraint functions $g, h$, its gradient or Jacobian requires the Hessians of the constraints.

For that seach direction a line search is performed, that additionally ensures that the constraints are further fulfilled.

# Input

  * `M`:      a manifold $\mathcal M$
  * `f`:      a cost function $f : \mathcal M → ℝ$ to minimize
  * `grad_f`: the gradient $\operatorname{grad} f : \mathcal M → T \mathcal M$ of $f$
  * `Hess_f`: the Hessian $\operatorname{Hess}f(p): T_p\mathcal M → T_p\mathcal M$, $X ↦ \operatorname{Hess}f(p)[X] = ∇_X\operatorname{grad}f(p)$
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: an initial value $p  ∈  \mathcal M$

or a [`ConstrainedManifoldObjective`](@ref) `cmo` containing `f`, `grad_f`, `Hess_f`, and the constraints

# Keyword arguments

The keyword arguments related to the constraints (the first eleven) are ignored if you pass a [`ConstrainedManifoldObjective`](@ref) `cmo`

  * `centrality_condition=missing`; an additional condition when to accept a step size. This can be used to ensure that the resulting iterate is still an interior point if you provide a check `(N,q) -> true/false`, where `N` is the manifold of the `step_problem`.
  * `equality_constraints=nothing`: the number $n$ of equality constraints.
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
  * `g=nothing`: the inequality constraints
  * `grad_g=nothing`: the gradient of the inequality constraints
  * `grad_h=nothing`: the gradient of the equality constraints
  * `gradient_range=nothing`: specify how gradients are represented, where `nothing` is equivalent to [`NestedPowerRepresentation`](@extref)
  * `gradient_equality_range=gradient_range`: specify how the gradients of the equality constraints are represented
  * `gradient_inequality_range=gradient_range`: specify how the gradients of the inequality constraints are represented
  * `h=nothing`: the equality constraints
  * `Hess_g=nothing`: the Hessian of the inequality constraints
  * `Hess_h=nothing`: the Hessian of the equality constraints
  * `inequality_constraints=nothing`: the number $m$ of inequality constraints.
  * `λ=ones(length(h(M, p)))`: the Lagrange multiplier with respect to the equality constraints $h$
  * `μ=ones(length(g(M, p)))`: the Lagrange multiplier with respect to the inequality constraints $g$
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: the retraction to use, defaults to the default set `M` with respect to the representation for `p` chosen.
  * `ρ=μ's / length(μ)`:  store the orthogonality `μ's/m` to compute the barrier parameter `β` in the sub problem.
  * `s=copy(μ)`: initial value for the slack variables
  * `σ=`[`calculate_σ`](@ref)`(M, cmo, p, μ, λ, s)`:  scaling factor for the barrier parameter `β` in the sub problem, which is updated during the iterations
  * `step_objective`: a [`ManifoldGradientObjective`](@ref) of the norm of the KKT vector field [`KKTVectorFieldNormSq`](@ref) and its gradient [`KKTVectorFieldNormSqGradient`](@ref)
  * `step_problem`: the manifold $\mathcal M × ℝ^m × ℝ^n × ℝ^m$ together with the `step_objective` as the problem the linesearch `stepsize=` employs for determining a step size
  * `step_state`: the [`StepsizeState`](@ref) with point and search direction
  * `stepsize` an [`ArmijoLinesearch`](@ref) with the [`InteriorPointCentralityCondition`](@ref) as additional condition to accept a step. Note that this step size operates on its own `step_problem`and `step_state`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenKKTResidualLess`](@ref)`(1e-8)`: a stopping criterion, by default depending on the residual of the KKT vector field or a maximal number of steps, which ever hits first.
  * `sub_kwargs=(;)`: keyword arguments to decorate the sub options, for example debug, that automatically respects the main solvers debug options (like sub-sampling) as well
  * `sub_objective`: The [`SymmetricLinearSystemObjective`](@ref) modelling the system of equations to use in the sub solver, includes the [`CondensedKKTVectorFieldJacobian`](@ref) $\mathcal A(X)$ and the [`CondensedKKTVectorField`](@ref) $b$ in $\mathcal A(X) + b = 0$ we aim to solve. This is used to setup the `sub_problem`. If you set the `sub_problem` directly, this keyword has no effect.
  * `sub_stopping_criterion=`[`StopAfterIteration`](@ref)`(manifold_dimension(M))`[`|`](@ref StopWhenAny)[`StopWhenRelativeResidualLess`](@ref)`(c,1e-8)`, where $c = \lVert b \rVert$ from the system to solve. This keyword is used in the `sub_state`. If you set that keyword diretly, this keyword does not have an effect.
  * `sub_problem`: combining the `sub_objective` and the tangent space at $(p,λ)$`on the manifold``\mathcal M × ℝ^n`` to a manopt problem.  This is the manifold and objective for the sub solver.
  * `sub_state=`[`ConjugateResidualState`](@ref): a state specifying the subsolver. This default is also decorated with the `sub_kwargs...`.
  * `vector_space=`[`Rn`](@ref Manopt.Rn) a function that, given an integer, returns the manifold to be used for the vector space components $ℝ^m,ℝ^n$
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M,p)`: th initial gradient with respect to `p`.
  * `Y=zero(μ)`:  the initial gradient with respct to `μ`
  * `Z=zero(λ)`:  the initial gradient with respct to `λ`
  * `W=zero(s)`:  the initial gradient with respct to `s`

As well as internal keywords used to set up these given keywords like `_step_M`, `_step_p`, `_sub_M`, `_sub_p`, and `_sub_X`, that should not be changed.

All other keyword arguments are passed to [`decorate_state!`](@ref) for state decorators or [`decorate_objective!`](@ref) for objective, respectively.

!!! note
    The `centrality_condition=mising` disables to check centrality during the line search, but you can pass [`InteriorPointCentralityCondition`](@ref)`(cmo, γ)`, where `γ` is a constant, to activate this check.


# Output

The obtained approximate constrained minimizer $p^*$. To obtain the whole final state of the solver, see [`get_solver_return`](@ref) for details, especially the `return_state=` keyword.
