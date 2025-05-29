```
DifferenceOfConvexState{Pr,St,P,T,SC<:StoppingCriterion} <:
           AbstractManoptSolverState
```

A struct to store the current state of the [`difference_of_convex_algorithm`])(@ref). It comes in two forms, depending on the realisation of the `subproblem`.

# Fields

  * `p`           the current iterate, a point on the manifold
  * `X`           the current subgradient, a tangent vector to `p`.
  * `sub_problem` problem for the subsolver
  * `sub_state`   state of the subproblem
  * `stop`        a functor inheriting from [`StoppingCriterion`](@ref) indicating when to stop.

For the sub task, a method to solve

$$
    \operatorname*{argmin}_{q∈\mathcal M}\ g(p) - ⟨X, \log_p q⟩
$$

is needed. Besides a problem and options, one can also provide a function and an [`AbstractEvaluationType`](@ref), respectively, to indicate a closed form solution for the sub task.

# Constructors

```
DifferenceOfConvexState(M, p, sub_problem, sub_state; kwargs...)
DifferenceOfConvexState(M, p, sub_solver; evaluation=InplaceEvaluation(), kwargs...)
```

Generate the state either using a solver from Manopt, given by an [`AbstractManoptProblem`](@ref) `sub_problem` and an [`AbstractManoptSolverState`](@ref) `sub_state`, or a closed form solution `sub_solver` for the sub-problem the function expected to be of the form `(M, p, X) -> q` or `(M, q, p, X) -> q`, where by default its [`AbstractEvaluationType`](@ref) `evaluation` is in-place of `q`. Here the elements passed are the current iterate `p` and the subgradient `X` of `h` can be passed to that function.

## further keyword arguments

  * `initial_vector=zero_vector` (`zero_vectoir(M,p)`) how to initialize the inner gradient tangent vector
  * `stopping_criterion`         a [`StopAfterIteration`](@ref)`(200)` a stopping criterion
