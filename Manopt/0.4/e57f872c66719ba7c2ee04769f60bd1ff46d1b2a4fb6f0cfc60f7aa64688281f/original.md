```
InteriorPointNewtonState <: AbstractHessianSolverState
```

# Fields

  * `λ`:           the Lagrange multiplier with respect to the equality constraints
  * `μ`:           the Lagrange multiplier with respect to the inequality constraints
  * `p`:           the current iterate
  * `s`:           the current slack variable
  * `sub_problem`: an [`AbstractManoptProblem`](@ref) problem for the subsolver
  * `sub_state`:   an [`AbstractManoptSolverState`](@ref) for the subsolver
  * `X`:           the current gradient with respect to `p`
  * `Y`:           the current gradient with respect to `μ`
  * `Z`:           the current gradient with respect to `λ`
  * `W`:           the current gradient with respect to `s`
  * `ρ`:           store the orthogonality `μ's/m` to compute the barrier parameter `β` in the sub problem
  * `σ`:           scaling factor for the barrier parameter `β` in the sub problem
  * `stop`: a [`StoppingCriterion`](@ref) indicating when to stop.
  * `retraction_method`: the retraction method to use on `M`.
  * `stepsize::`[`Stepsize`](@ref): the stepsize to use
  * `step_problem`: an [`AbstractManoptProblem`](@ref) storing the manifold and objective for the line search
  * `step_state`: storing iterate and search direction in a state for the line search, see [`StepsizeState`](@ref)

# Constructor

```
InteriorPointNewtonState(
    M::AbstractManifold,
    cmo::ConstrainedManifoldObjective,
    p,
    sub_problem::Pr,
    sub_state::St;
    kwargs...
)
```

Initialize the state, where both the [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) and the [`ConstrainedManifoldObjective`](@ref) are used to fill in reasonable defaults for the keywords.

# Input

  * `M`:           a Riemannian manifold
  * `cmo`:         a [`ConstrainedManifoldObjective`](@ref)
  * `p`:           a point on `M` as the inital point of the algorithm
  * `sub_problem`: an [`AbstractManoptProblem`](@ref) problem for the sub solver
  * `sub_state`:   an [`AbstractManoptSolverState`](@ref) for the sub solver

# Keyword arguments

Let `m` and `n` denote the number of inequality and equality constraints, respectively

  * `μ=ones(m)`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M,p)`
  * `Y=zero(μ)`
  * `λ=zeros(n)`
  * `Z=zero(λ)`
  * `s=ones(m)`
  * `W=zero(s)`
  * `ρ=μ's/m`
  * `σ=`[`calculate_σ`](@ref)`(M, cmo, p, μ, λ, s)`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-8)`
  * `retraction_method=default_retraction_method(M, typeof(p))`
  * `step_objective=`[`ManifoldGradientObjective`](@ref)`(`[`KKTVectorFieldNormSq`](@ref)`(cmo)`, [`KKTVectorFieldNormSqGradient`](@ref)`(cmo)`; evaluation=[`InplaceEvaluation`](@ref)`())`
  * `vector_space=`[`Rn`](@ref Manopt.Rn): a function that, given an integer, returns the manifold to be used for the vector space components $ℝ^m,ℝ^n$
  * `step_problem`: wrap the manifold $\mathcal M × ℝ^m × ℝ^n × ℝ^m$
  * `step_state`: the [`StepsizeState`](@ref) with point and search direction
  * `stepsize`: an [`ArmijoLinesearch`](@ref) with the [`InteriorPointCentralityCondition`](@ref) as additional condition to accept a step. Note that this step size operates on its own `step_problem`and `step_state`

and internally `_step_M` and `_step_p` for the manifold and point in the stepsize.
