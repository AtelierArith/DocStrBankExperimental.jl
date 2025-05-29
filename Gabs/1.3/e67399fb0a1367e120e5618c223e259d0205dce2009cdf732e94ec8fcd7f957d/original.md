```
changebasis(::SymplecticBasis, state::GaussianState)
```

Change the symplectic basis of a Gaussian state.

# Example

```jldoctest
julia> st = squeezedstate(QuadBlockBasis(2), 1.0, 2.0)
GaussianState for 2 modes.
  symplectic basis: QuadBlockBasis
mean: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
covariance: 4×4 Matrix{Float64}:
  5.2715    0.0      -3.29789   0.0
  0.0       5.2715    0.0      -3.29789
 -3.29789   0.0       2.25289   0.0
  0.0      -3.29789   0.0       2.25289

julia> changebasis(QuadPairBasis, st)
GaussianState for 2 modes.
  symplectic basis: QuadPairBasis
mean: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
covariance: 4×4 Matrix{Float64}:
  5.2715   -3.29789   0.0       0.0
 -3.29789   2.25289   0.0       0.0
  0.0       0.0       5.2715   -3.29789
  0.0       0.0      -3.29789   2.25289
```
