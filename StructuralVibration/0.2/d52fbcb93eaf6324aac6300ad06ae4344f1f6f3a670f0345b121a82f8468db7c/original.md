```
ModalFRFProblem(ωn, ξn, freq, ϕo, ϕe)
```

Structure containing the data feeding the modal solver for calculating an FRF

**Fields**

  * `ωn::Vector{Real}`: Natural angular frequencies
  * `ξn::Vector{Real}`: Modal damping ratios
  * `freq::AbstractRange`: Frequencies of interest
  * `ϕe::AbstractMatrix`: Mode shapes at excitation points
  * `ϕo::AbstractMatrix`: Mode shapes at observation points

**Note** The mode shapes must be mass-normalized
