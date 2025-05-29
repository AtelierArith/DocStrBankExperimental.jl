Defines a Gaussian state for an N-mode bosonic system over a 2N-dimensional phase space.

## Fields

  * `basis`: Symplectic basis for Gaussian state.
  * `mean`: The mean vector of length 2N.
  * `covar`: The covariance matrix of size 2N x 2N.
  * `ħ = 2`: Reduced Planck's constant.

## Example

```jldoctest
julia> coherentstate(QuadPairBasis(1), 1.0+im)
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 2.0
 2.0
covariance: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
