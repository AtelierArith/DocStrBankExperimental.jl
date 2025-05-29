```
ModalFreqProblem(ωn, ξn, Fn, freq, ϕo)
```

Structure containing the data feeding the modal solver for calculating the frequency response by modal approach

**Fields**

  * `ωn::Vector{Real}`: Natural angular frequencies
  * ξn::Vector{Real}: Modal damping ratios
  * `Ln::AbstractMatrix`: Modal participation factors
  * `freq::AbstractRange`: Frequencies of interest
  * `ϕo::Matrix{Real}`: Mode shapes at observation points
