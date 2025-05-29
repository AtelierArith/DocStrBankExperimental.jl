```
LevenbergMarquardtState{P,T} <: AbstractGradientSolverState
```

Describes a Gradient based descent algorithm, with

# Fields

A default value is given in brackets if a parameter can be left out in initialization.

  * `x`:                     a point (of type `P`) on a manifold as starting point
  * `stop`:                  (`StopAfterIteration(200) | StopWhenGradientNormLess(1e-12) | StopWhenStepsizeLess(1e-12)`) a [`StoppingCriterion`](@ref)
  * `retraction_method`:     (`default_retraction_method(M, typeof(p))`) the retraction to use, defaults to the default set for your manifold.
  * `residual_values`       value of $F$ calculated in the solver setup or the previous iteration
  * `residual_values_temp`  value of $F$ for the current proposal point
  * `jacF`                  the current Jacobian of $F$
  * `gradient`              the current gradient of $F$
  * `step_vector`           the tangent vector at `x` that is used to move to the next point
  * `last_stepsize`         length of `step_vector`
  * `η`                     Scaling factor for the sufficient cost decrease threshold required to accept new proposal points. Allowed range: `0 < η < 1`.
  * `damping_term`          current value of the damping term
  * `damping_term_min`      initial (and also minimal) value of the damping term
  * `β`                     parameter by which the damping term is multiplied when the current new point is rejected
  * `expect_zero_residual`:  (`false`) if true, the algorithm expects that the value of the residual (objective) at minimum is equal to 0.

# Constructor

```
LevenbergMarquardtState(M, initialX, initial_residual_values, initial_jacF; initial_vector), kwargs...)
```

Generate Levenberg-Marquardt options.

# See also

[`gradient_descent`](@ref), [`LevenbergMarquardt`](@ref)
