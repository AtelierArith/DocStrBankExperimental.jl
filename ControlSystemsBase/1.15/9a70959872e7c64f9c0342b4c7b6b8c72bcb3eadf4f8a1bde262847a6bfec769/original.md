```
stepinfo(res::SimResult; y0 = nothing, yf = nothing, settling_th = 0.02, risetime_th = (0.1, 0.9))
```

Compute the step response characteristics for a simulation result. The following information is computed and stored in a [`StepInfo`](@ref) struct:

  * `y0`: The initial value of the response
  * `yf`: The final value of the response
  * `stepsize`: The size of the step
  * `peak`: The peak value of the response
  * `peaktime`: The time at which the peak occurs
  * `overshoot`: The percentage overshoot of the response
  * `undershoot`: The percentage undershoot of the response. If the step response never reaches below the initial value, the undershoot is zero.
  * `settlingtime`: The time at which the response settles within `settling_th` of the final value
  * `settlingtimeind`: The index at which the response settles within `settling_th` of the final value
  * `risetime`: The time at which the response rises from `risetime_th[1]` to `risetime_th[2]` of the final value

# Arguments:

  * `res`: The result from a simulation using [`step`](@ref) (or [`lsim`](@ref))
  * `y0`: The initial value, if not provided, the first value of the response is used.
  * `yf`: The final value, if not provided, the last value of the response is used. The simulation must have reached steady-state for an automatically computed value to make sense. If the simulation has not reached steady state, you may provide the final value manually.
  * `settling_th`: The threshold for computing the settling time. The settling time is the time at which the response settles within `settling_th` of the final value.
  * `risetime_th`: The lower and upper threshold for computing the rise time. The rise time is the time at which the response rises from `risetime_th[1]` to `risetime_th[2]` of the final value.

# Example:

```julia
G = tf([1], [1, 1, 1])
res = step(G, 15)
si = stepinfo(res)
plot(si)
```
