```
DP5Solver(f, x, y; kw...)
```

Create a 5th Order Dormand-Prince solver object to solve the ODE problem `y' = f(x, y)`.

# Examples

```julia
julia> fcn(x, y, f)
            f[1] = 0.85y[1]
        end

julia> solver = DP5Solver(fcn, 0.0, [19.0]; atol = 1e-10, rtol = 1e-10)
```

# Arguments

  * `f`: The function representing the ODE, should be in the form `f(x, y, f)`.
  * `x`: The starting time point of the ODE problem.
  * `y`: The initial value of the ODE in vector form

# Keyword Arguments

  * `atol`: Absolute Tolerance. Default is 1e-10
  * `rtol`: Relative Tolerance. Default is 1e-10
  * `uround`: Rounding unit, default is eps(T) where T <: Real.
  * `safety_factor`: Safety factor in step size prediction, default is 0.9.
  * Step Size Selection parameters, with the new step size being subject to the constraint: `step_size_selection_one <= new_step/old_step <= step_size_selection_two`

      * `step_size_selection_one`: Defaut is 0.2
      * `step_size_selection_two`: Default is 10.0
  * `beta`: Beta for stabilized step size control. Large values of beta (<= 0.1) make step size control more stable.
  * `maximal_step_size`: The largest the step size can be. Default is 0.0, which internally translates to `xend - x`.
  * `initial_step_size`: Initial step size, default is 0.0. An initial guess is computed internally.
  * `maximum_allowed_steps`: Maximum number of allowed steps, default is 100000.
  * `print_error_messages`: Whether to print error messages, default is true.
  * `stiffness_test_activation_step`: After integer multiples of this number of steps, perform stiffness detection. Default is 1000.
