Constant first-order change approximation to determine initial step length.

** This requires that the optimization algorithm stores dphi0 from the previous iteration ** (dphi0*previous = real(dot(∇f*{k-1}, s_{k-1})), where s is the step direction.

This is meant for methods that do not produce well-scaled search directions, such as Gradient Descent and (variations of) Conjugate Gradient methods. See the discussion in Nocedal and Wright, 2nd ed, p. 59 on "Initial Step Length"

This procedure have several arguments, with the following defaults.

  * `α0       = 1.0`.         The initial step size at the first iteration.
  * `αmin     = 1e-12`.       The minimum initial step size. (Default arbitrary).
  * `αmax     = 1.0`.         The maximum initial step size.
  * `ρ        = 0.25`.        Maximum decrease from previous iteration, `αinit ≥ α_{k-1}`. (Default arbitrary).
  * `snap2one = (0.75, Inf)`. Set all values within this (closed) interval to 1.0. (Default arbitrary).

If αmax ≠ 1.0, then you should consider to ensure that snap2one[2] < αmax.
