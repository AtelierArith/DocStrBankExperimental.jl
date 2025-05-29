```
stopChamber_MT(out, u::Vector{Float64}, t::Float64, int, sw::SW{Int8}, param::Param{Float64})
```

Define the stopping criteria for an ODE solver that simulates a magma chamber.

## Arguments

  * `out`: An array where the function should save the condition value at the right index. The maximum index of `out` should be specified in the `len` property of `callback`, which allows for a chain of `len` events, triggering the `ith` event when `out[i] = 0`. The function returns the value of `out[8]` as the last condition. Checking Event Handling and Callback Functions page of `DifferentialEquations.jl` for more details.
  * `u`: A vector containing the state of the system at time `t`.
  * `t`: The current time of the ODE solver.
  * `int`: The current state of the integrator. It's format is from the DifferentialEquations.jl package
  * `sw`: A custom parameter used to control simulation behavior.
  * `param`: A custom parameter containing physical constants and other model parameters.

The arguments `out`, `u`, `t`, and `int` are from the DifferentialEquations.jl package. These argument formats are specific to the DifferentialEquations.jl package.

## Returns

The `out` array is modified in-place to contain the condition values at the current state of the system. The function computes several quantities based on the current state of the system and the model parameters, such as the crystal fraction, the maximum amount of exsolved fluid, and the amount of CO2 in the melt. It then uses these values to calculate the condition values to be stored in the `out` array, as follows:

  * `out[1]`: the crystal fraction.
  * `out[2]`: the ratio of crystal fraction to liquid fraction, minus 0.8.
  * `out[3]`: if an eruption is not occurring, the pressure difference between the lithostatic pressure and the current pressure, minus the critical pressure difference. Otherwise, negative the critical pressure difference.
  * `out[4]`: if an eruption is occurring, the lithostatic pressure minus the current pressure. Otherwise, negative the critical pressure difference.
  * `out[5]`: the crystal fraction minus 0.5.
  * `out[6]`: the difference between the amount of water in the melt and the maximum amount of exsolved fluid.
  * `out[7]`: negative the difference between the initial lithostatic pressure and the current pressure plus the critical pressure difference.
  * `out[8]`: the difference between the amount of CO2 in the melt and the saturation concentration.

Note that the `out` and `u` arguments are in the format expected by the DifferentialEquations.jl package, and the function is intended to be used as a condition for a callback function.
