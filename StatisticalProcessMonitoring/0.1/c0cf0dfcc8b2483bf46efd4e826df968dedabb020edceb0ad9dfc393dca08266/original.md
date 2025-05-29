```
OneSidedEWMA(λ, value, upw::Bool)
```

OneSidedEWMA statistic with design parameter `λ` and initial value `value`.

The update mechanism based on a new observation `x` is given by:

  * if `upw == true`, then $C_t = \max\{0, (1-λ)\cdot C_{t-1} + λ\cdot x\}$;
  * if `upw == true`, then $C_t = \min\{0, (1-λ)\cdot C_{t-1} + λ\cdot x\}$;

### Arguments

  * `λ::Float64`: The smoothing constant. Default is `0.1`.
  * `value::Float64`: The current value of the statistic. Default is `0.0`.
  * `upw::Bool`: Whether the statistic should monitor increases (`true`) or decrease (`falses`) in the process mean. Default is `true`.
