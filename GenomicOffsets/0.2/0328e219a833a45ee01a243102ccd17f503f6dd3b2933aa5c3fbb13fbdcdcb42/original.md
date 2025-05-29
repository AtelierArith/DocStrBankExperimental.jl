```
RidgeLFMM(Y::Matrix{T}, X::Matrix{T}, K::Int, λ::Float64) where T<:Real
```

Ridge solutions for the Linear Fixed Effects Mixed Model (LFMM) as described by Caye et al. (2019).

$$
Y = X B^T + W = X B^T + U V^T
$$

# Arguments

  * `Y`: A centered genotype matrix of size NxL.
  * `X`: Environmental matrix of size NxP.
  * `K`: Number of latent factors.
  * `λ`: Regularization parameter (by 1e-5)
  * `center`: If true, both the genotype matrix and the environmental matrix are centered. If false, both matrices are assumed to be centered.

# Returns

  * A `LFMM{T<:Real}` data structure with the latent factors `U`, `Vt`, and the effect sizes `Bt`.
