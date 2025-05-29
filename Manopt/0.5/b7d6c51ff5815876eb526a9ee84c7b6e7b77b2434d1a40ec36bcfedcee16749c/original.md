```
InteriorPointNewtonState{P,T} <: AbstractHessianSolverState
```

# Fields

  * `λ`:           the Lagrange multiplier with respect to the equality constraints
  * `μ`:           the Lagrange multiplier with respect to the inequality constraints
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `s`:           the current slack variable
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `X`:           the current gradient with respect to `p`
  * `Y`:           the current gradient with respect to `μ`
  * `Z`:           the current gradient with respect to `λ`
  * `W`:           the current gradient with respect to `s`
  * `ρ`:           store the orthogonality `μ's/m` to compute the barrier parameter `β` in the sub problem
  * `σ`:           scaling factor for the barrier parameter `β` in the sub problem
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `step_problem`: an [`AbstractManoptProblem`](@ref) storing the manifold and objective for the line search
  * `step_state`: storing iterate and search direction in a state for the line search, see [`StepsizeState`](@ref)

# Constructor

```
InteriorPointNewtonState(
    M::AbstractManifold,
    cmo::ConstrainedManifoldObjective,
    sub_problem::Pr,
    sub_state::St;
    kwargs...
)
```

Initialize the state, where both the [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) and the [`ConstrainedManifoldObjective`](@ref) are used to fill in reasonable defaults for the keywords.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$
  * `cmo`:         a [`ConstrainedManifoldObjective`](@ref)
  * `sub_problem`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.

# Keyword arguments

Let `m` and `n` denote the number of inequality and equality constraints, respectively

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `μ=ones(m)`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M,p)`
  * `Y=zero(μ)`
  * `λ=zeros(n)`
  * `Z=zero(λ)`
  * `s=ones(m)`
  * `W=zero(s)`
  * `ρ=μ's/m`
  * `σ=`[`calculate_σ`](@ref)`(M, cmo, p, μ, λ, s)`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-8)`: a functor indicating that the stopping criterion is fulfilled
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `step_objective=`[`ManifoldGradientObjective`](@ref)`(`[`KKTVectorFieldNormSq`](@ref)`(cmo)`, [`KKTVectorFieldNormSqGradient`](@ref)`(cmo)`; evaluation=[`InplaceEvaluation`](@ref)`())`
  * `vector_space=`[`Rn`](@ref Manopt.Rn): a function that, given an integer, returns the manifold to be used for the vector space components $ℝ^m,ℝ^n$
  * `step_problem`: wrap the manifold $\mathcal M × ℝ^m × ℝ^n × ℝ^m$
  * `step_state`: the [`StepsizeState`](@ref) with point and search direction
  * `stepsize=`[`ArmijoLinesearch`](@ref)`()`: a functor inheriting from [`Stepsize`](@ref) to determine a step size with the [`InteriorPointCentralityCondition`](@ref) as additional condition to accept a step

and internally `_step_M` and `_step_p` for the manifold and point in the stepsize.
