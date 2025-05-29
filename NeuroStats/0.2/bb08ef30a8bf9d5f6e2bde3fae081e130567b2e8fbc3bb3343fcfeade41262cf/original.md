```
ba(x, y; <keyword arguments>)
```

Calculate Bland-Altman comparison between two clinical measurements.

# Arguments

  * `x::AbstractVector`
  * `y::AbstractVector`
  * `la::FLoat64=0.95`: 95% limits of agreement for each comparison (average difference ± 1.96 standard deviation of the difference)

# Returns

  * `m::Float64`: mean difference
  * `s_u::Float64`: +1.96 (for default la) standard deviation of the difference
  * `s_d::Float64`: -1.96 (for default la) standard deviation of the difference

# Notes

To plot the Bland-Altman plot: `p = hline([0, m]); hline!([0, s_u]); hline!([0, s-d])`
