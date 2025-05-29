```
friedman(m)
```

Estimate Friedman's nonparametric two-way analysis of variance (and Kendall's coefficient of concordance, normalized Friedman's Q statistics).

# Arguments

  * `m::AbstractArray`: values × groups

# Returns

Named tuple containing:

  * `q::Float64`: Friedman's Q statistics
  * `w::Float64`: Kendall's coefficient of concordance
  * `p::Float64`: p value

# Notes

  * H0 (Friedman) is that the treatments are equal
  * H0 (Kendall) is that there is agreement between rankings or test results
  * Kendall's coefficient of concordance ranges from 0 to 1, with 0 meaning no agreement across raters (judges)
