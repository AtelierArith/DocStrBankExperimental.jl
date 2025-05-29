```
StepInfo
```

Computed using [`stepinfo`](@ref)

# Fields:

  * `y0`: The initial value of the step response.
  * `yf`: The final value of the step response.
  * `stepsize`: The size of the step.
  * `peak`: The peak value of the step response.
  * `peaktime`: The time at which the peak occurs.
  * `overshoot`: The overshoot of the step response.
  * `settlingtime`: The time at which the step response has settled to within `settling_th` of the final value.
  * `settlingtimeind::Int`: The index at which the step response has settled to within `settling_th` of the final value.
  * `risetime`: The time at which the response rises from `risetime_th[1]` to `risetime_th[2]` of the final value
  * `i10::Int`: The index at which the response reaches `risetime_th[1]`
  * `i90::Int`: The index at which the response reaches `risetime_th[2]`
  * `res::SimResult{SR}`: The simulation result used to compute the step response characteristics.
  * `settling_th`: The threshold used to compute `settlingtime` and `settlingtimeind`.
  * `risetime_th`: The thresholds used to compute `risetime`, `i10`, and `i90`.
