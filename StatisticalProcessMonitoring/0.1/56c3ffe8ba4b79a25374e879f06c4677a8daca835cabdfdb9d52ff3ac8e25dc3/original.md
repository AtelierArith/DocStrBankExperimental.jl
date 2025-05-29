```
WCUSUM <: AbstractStatistic
```

A weighted cumulative sum statistic.

# Arguments

  * `k::Float64`: The allowance constant of the CUSUM used for calculating the WCUSUM statistic. Default is 1.0.
  * `λ::Float64`: The smoothing constant for updating the estimate of the fault signature. Must be a value between 0 and 1. Default is 0.2.
  * `value::Float64`: The initial value of the weighted cumulative sum statistic. Default is 0.0.
  * `Q::Float64`: The residual value of the weighted cumulative sum. Default is 0.0.
  * `upw::Bool`: Whether to monitor increases in the mean (`true`) or decreases (`false`). Default is `true`.

# References

Shu, L., Jiang, W., & Tsui, K.-L. (2008). A Weighted CUSUM Chart for Detecting Patterned Mean Shifts. Journal of Quality Technology, 40(2), 194-213. https://doi.org/10.1080/00224065.2008.11917725

# Examples

```julia
stat = WCUSUM()
get_design(stat)            # returns [1.0, 0.2]
update_statistic(stat, 3.0) # returns 1.2
stat.Q                      # returns 0.6
```
