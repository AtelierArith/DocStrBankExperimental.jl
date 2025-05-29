```
LevenbergMarquardtState{P,T} <: AbstractGradientSolverState
```

Describes a Gradient based descent algorithm, with

# Fields

A default value is given in brackets if a parameter can be left out in initialization.

  * `p::P`: a point on the manifold $\mathcal M$storing the current iterate
  * `retraction_method::AbstractRetractionMethod`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `residual_values`:      value of $F$ calculated in the solver setup or the previous iteration
  * `residual_values_temp`: value of $F$ for the current proposal point
  * `stop::StoppingCriterion`: a functor indicating that the stopping criterion is fulfilled
  * `jacobian`:                 the current Jacobian of $F$
  * `gradient`:             the current gradient of $F$
  * `step_vector`:          the tangent vector at `x` that is used to move to the next point
  * `last_stepsize`:        length of `step_vector`
  * `η`:                    Scaling factor for the sufficient cost decrease threshold required to accept new proposal points. Allowed range: `0 < η < 1`.
  * `damping_term`:         current value of the damping term
  * `damping_term_min`:     initial (and also minimal) value of the damping term
  * `β`:                    parameter by which the damping term is multiplied when the current new point is rejected
  * `expect_zero_residual`: if true, the algorithm expects that the value of the residual (objective) at minimum is equal to 0.
  * `linear_subsolver!`:    a function with three arguments `sk, JJ, grad_f_c``that solves the linear subproblem`sk .= JJ \ grad*f*c`, where`JJ`is (up to numerical issues) a symmetric positive definite matrix. Default value is [`default*lm*lin_solve!`](@ref).

# Constructor

```
LevenbergMarquardtState(M, initial_residual_values, initial_jacobian; kwargs...)
```

Generate the Levenberg-Marquardt solver state.

# Keyword arguments

The following fields are keyword arguments

  * `β=5.0`
  * `damping_term_min=0.1`
  * `η=0.2`,
  * `expect_zero_residual=false`
  * `initial_gradient=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-12)`[`|`](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-12)`: a functor indicating that the stopping criterion is fulfilled

# See also

[`gradient_descent`](@ref), [`LevenbergMarquardt`](@ref)
