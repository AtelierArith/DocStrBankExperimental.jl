```
LanczosState{P,T,SC,B,I,R,TM,V,Y} <: AbstractManoptSolverState
```

Solve the adaptive regularized subproblem with a Lanczos iteration

# Fields

  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `stop_newton::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilledused for the inner Newton iteration
  * `σ`:               the current regularization parameter
  * `X`:               the Iterate
  * `Lanczos_vectors`: the obtained Lanczos vectors
  * `tridig_matrix`:   the tridiagonal coefficient matrix T
  * `coefficients`:    the coefficients $y_1,...y_k$ that determine the solution
  * `Hp`:              a temporary tangent vector containing the evaluation of the Hessian
  * `Hp_residual`:     a temporary tangent vector containing the residual to the Hessian
  * `S`:               the current obtained / approximated solution

# Constructor

```
LanczosState(TpM::TangentSpace; kwargs...)
```

## Keyword arguments

  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$as the iterate
  * `maxIterLanzcos=200`: shortcut to set the maximal number of iterations in the `stopping_crtierion=`
  * `θ=0.5`: set the parameter in the [`StopWhenFirstOrderProgress`](@ref) within the default `stopping_criterion=`.
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(maxIterLanczos)`[`|`](@ref StopWhenAny)[`StopWhenFirstOrderProgress`](@ref)`(θ)`: a functor indicating that the stopping criterion is fulfilled
  * `stopping_criterion_newton=`[`StopAfterIteration`](@ref)`(200)`: a functor indicating that the stopping criterion is fulfilled used for the inner Newton iteration
  * `σ=10.0`: specify the regularization parameter
