```
ArmijoLinesearch(; kwargs...)
ArmijoLinesearch(M::AbstractManifold; kwargs...)
```

Specify a step size that performs an Armijo line search. Given a Function $f:\mathcal M→ℝ$ and its Riemannian Gradient $\operatorname{grad}f: \mathcal M→T\mathcal M$, the curent point $p∈\mathcal M$ and a search direction $X∈T_{p}\mathcal M$.

Then the step size $s$ is found by reducing the initial step size $s$ until

$$
f(\operatorname{retr}_p(sX)) ≤ f(p) - τs ⟨ X, \operatorname{grad}f(p) ⟩_p
$$

is fulfilled. for a sufficient decrease value $τ ∈ (0,1)$.

To be a bit more optimistic, if $s$ already fulfils this, a first search is done, **increasing** the given $s$ until for a first time this step does not hold.

Overall, we look for step size, that provides *enough decrease*, see [Boumal:2023; p. 58](@cite) for more information.

# Keyword arguments

  * `additional_decrease_condition=(M, p) -> true`: specify an additional criterion that has to be met to accept a step size in the decreasing loop
  * `additional_increase_condition::IF=(M, p) -> true`: specify an additional criterion that has to be met to accept a step size in the (initial) increase loop
  * `candidate_point=allocate_result(M, rand)`: speciy a point to be used as memory for the candidate points.
  * `contraction_factor=0.95`: how to update $s$ in the decrease step
  * `initial_stepsize=1.0``: specify an initial step size
  * `initial_guess=`[`armijo_initial_guess`](@ref): Compute the initial step size of a line search based on this function. The funtion required is `(p,s,k,l) -> α` and computes the initial step size $α$ based on a [`AbstractManoptProblem`](@ref) `p`, [`AbstractManoptSolverState`](@ref) `s`, the current iterate `k` and a last step size `l`.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stop_when_stepsize_less=0.0`: a safeguard, stop when the decreasing step is below this (nonnegative) bound.
  * `stop_when_stepsize_exceeds=max_stepsize(M)`: a safeguard to not choose a too long step size when initially increasing
  * `stop_increasing_at_step=100`: stop the initial increasing loop after this amount of steps. Set to `0` to never increase in the beginning
  * `stop_decreasing_at_step=1000`: maximal number of Armijo decreases / tests to perform
  * `sufficient_decrease=0.1`: the sufficient decrease parameter $τ$

For the stop safe guards you can pass `:Messages` to a `debug=` to see `@info` messages when these happen.

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`ArmijoLinesearchStepsize`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

