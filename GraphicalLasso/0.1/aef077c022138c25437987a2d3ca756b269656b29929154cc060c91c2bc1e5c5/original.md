```
ebic(θ, ll, obs, thr, γ)
```

Calculates the Extended Bayesian Information Criterion (EBIC) for a given precision matrix `θ`. From the paper by Foygel and Drton (2010), the EBIC is defined as:

$\text{EBIC} = -2 \times \text{Log-likelihood} + \log(n) \times \mathbf{E} + 4 \times \gamma \times \mathbf{E} \times \log(p)$

where:

  * n is the number of observations.
  * p is the number of variables.
  * gamma is a tuning parameter.
  * The number of edges is calculated as the count of entries in theta that exceed a given threshold.

# Arguments

  * `θ::AbstractMatrix`: Precision matrix.
  * `ll::Real`: Log-likelihood.
  * `obs::Int`: Number of observations.
  * `thr::Real`: Threshold value for counting edges.
  * `γ::Real`: EBIC tuning parameter.

# Returns

  * `Real`: EBIC value.
