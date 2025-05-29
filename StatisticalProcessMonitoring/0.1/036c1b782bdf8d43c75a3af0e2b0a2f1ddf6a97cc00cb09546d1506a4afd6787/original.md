```
CUSUM(k, value, upw::Bool)
```

CUSUM statistic with design parameter `k` and initial value `value`.

The update mechanism based on a new observation `x` is given by:

  * if `upw == true`, then $C_t = \max\{0, C_{t-1} + x - k\}$;
  * if `upw == false`, then $C_t = \min\{0, C_{t-1} + x + k\}$.

### Arguments

  * `k::Float64`: The allowance constant of the CUSUM statistic. Defaults to `1.0`.
  * `value::Float64`: The current value of the cumulative sum. Defaults to `0.0`.
  * `upw::Bool`: A boolean indicating whether the CUSUM statistic is increasing or decreasing. Defaults to `true`.

### References

Page, E. S. (1954). Continuous Inspection Schemes. Biometrika, 41(1/2), 100. https://doi.org/10.2307/2333009
