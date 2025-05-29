```
MK_statistics(T0::Vector, Tk::Vector{Vector}; filter_method)
```

Computes the multiple knockoff statistics kappa, tau, and W. 

# Inputs

  * `T0`: p-vector of importance score for original variables
  * `Tk`: Vector storing T1, ..., Tm, where Ti is importance scores for    the `i`th knockoff copy
  * `filter_method`: Either `Statistics.median` (default) or max (original    function used in 2019 Gimenez and Zou)

# output

  * `κ`: Index of the most significant feature (`κ[i] = 0` if original feature most    important, otherwise `κ[i] = k` if the `k`th knockoff is most important)
  * `τ`: `τ[i]` stores the most significant statistic among original and knockoff   variables minus `filter_method()` applied to the remaining statistics.
  * `W`: coefficient difference statistic `W[i] = abs(T0[i]) - abs(Tk[i])`
