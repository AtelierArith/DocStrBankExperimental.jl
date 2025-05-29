```
DifferenceOfConvexState{Pr,St,P,T,SC<:StoppingCriterion} <:
           AbstractManoptSolverState
```

A struct to store the current state of the [`difference_of_convex_algorithm`])(@ref). It comes in two forms, depending on the realisation of the `subproblem`.

# Fields

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing a subgradient at the current iterate
  * `sub_problem::Union{AbstractManoptProblem, F}`:  specify a problem for a solver or a closed form solution function, which can be allocating or in-place.
  * `sub_state::Union{AbstractManoptProblem, F}`:  a state to specify the sub solver to use. For a closed form solution, this indicates the type of function.
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled

The sub task consists of a method to solve

$$
    \operatorname*{arg\,min}_{q∈\mathcal M}\ g(p) - ⟨X, \log_p q⟩
$$

is needed. Besides a problem and a state, one can also provide a function and an [`AbstractEvaluationType`](@ref), respectively, to indicate a closed form solution for the sub task.

# Constructors

```
DifferenceOfConvexState(M, sub_problem, sub_state; kwargs...)
DifferenceOfConvexState(M, sub_solver; evaluation=InplaceEvaluation(), kwargs...)
```

Generate the state either using a solver from Manopt, given by an [`AbstractManoptProblem`](@ref) `sub_problem` and an [`AbstractManoptSolverState`](@ref) `sub_state`, or a closed form solution `sub_solver` for the sub-problem the function expected to be of the form `(M, p, X) -> q` or `(M, q, p, X) -> q`, where by default its [`AbstractEvaluationType`](@ref) `evaluation` is in-place of `q`. Here the elements passed are the current iterate `p` and the subgradient `X` of `h` can be passed to that function.

## further keyword arguments

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`: a functor indicating that the stopping criterion is fulfilled
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector
