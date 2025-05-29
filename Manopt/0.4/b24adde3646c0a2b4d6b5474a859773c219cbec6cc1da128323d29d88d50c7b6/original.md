```
QuasiNewtonState <: AbstractManoptSolverState
```

These Quasi Newton [`AbstractManoptSolverState`](@ref) represent any quasi-Newton based method and can be used with any update rule for the direction.

# Fields

  * `p`                             the current iterate, a point on a manifold
  * `X`                             the current gradient
  * `sk`                            the current step
  * `yk`                            the current gradient difference
  * `direction_update`              an [`AbstractQuasiNewtonDirectionUpdate`](@ref) rule.
  * `nondescent_direction_behavior` a `Symbol` to specify how to handle direction that are not descent ones.
  * `retraction_method`             an `AbstractRetractionMethod`
  * `stepsize`                      a [`Stepsize`](@ref)
  * `stop`                          a [`StoppingCriterion`](@ref)

as well as for internal use

  * `p_old`                      the last iterate
  * `η`                          the current update direction
  * `X_old`                      the last gradient
  * `nondescent_direction_value` the value from the last inner product from checking for descent directions

# Constructor

```
QuasiNewtonState(
    M::AbstractManifold,
    x;
    initial_vector=zero_vector(M,x),
    direction_update::D=QuasiNewtonLimitedMemoryDirectionUpdate(M, x, InverseBFGS(), 20;
        vector_transport_method=vector_transport_method,
    )
    stopping_criterion=StopAfterIteration(1000) | StopWhenGradientNormLess(1e-6),
    retraction_method::RM=default_retraction_method(M, typeof(p)),
    vector_transport_method::VTM=default_vector_transport_method(M, typeof(p)),
    stepsize=default_stepsize(M; QuasiNewtonState)
)
```

# See also

[`quasi_Newton`](@ref)
