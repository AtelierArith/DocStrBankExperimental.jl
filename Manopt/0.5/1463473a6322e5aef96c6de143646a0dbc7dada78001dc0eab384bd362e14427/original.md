```
QuasiNewtonState <: AbstractManoptSolverState
```

The [`AbstractManoptSolverState`](@ref) represent any quasi-Newton based method and stores all necessary fields.

# Fields

  * `direction_update`:              an [`AbstractQuasiNewtonDirectionUpdate`](@ref) rule.
  * `η`:                             the current update direction
  * `nondescent_direction_behavior`: a `Symbol` to specify how to handle direction that are not descent ones.
  * `nondescent_direction_value`:    the value from the last inner product from checking for descent directions
  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `p_old`:                         the last iterate
  * `preconditioner`                 an [`QuasiNewtonPreconditioner`](@ref)
  * `sk`:                            the current step
  * `yk`:                            the current gradient difference
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize::Stepsize`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `X::T`: a tangent vector at the point $p$ on the manifold $\mathcal M$storing the gradient at the current iterate
  * `X_old`:                         the last gradient

# Constructor

```
QuasiNewtonState(M::AbstractManifold, p; kwargs...)
```

Generate the Quasi Newton state on the manifold `M` with start point `p`.

## Keyword arguments

  * `direction_update=`[`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref)`(M, p, InverseBFGS(), memory_size; vector_transport_method=vector_transport_method)`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: a functor indicating that the stopping criterion is fulfilled
  * `initial_scale=1.0`: a realtive initial scale. By default deactivated when using a preconditioner.
  * `memory_size=20`: a shortcut to set the memory in the default direction update
  * `preconditioner::Union{`[`QuasiNewtonPreconditioner`](@ref)`, Nothing} = nothing` specify a preconditioner or deactivate by passing `nothing`.
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`default_stepsize`](@ref)`(M, QuasiNewtonState)`: a functor inheriting from [`Stepsize`](@ref) to determine a step size
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$to specify the representation of a tangent vector

# See also

[`quasi_Newton`](@ref)
