```
tensor(state1::GaussianState, state2::GaussianState)
```

tensor product of Gaussian states, which can also be called with `⊗`.

## Example

```jldoctest
julia> basis = QuadPairBasis(1);

julia> coherentstate(basis, 1.0+im) ⊗ thermalstate(basis, 2)
GaussianState for 2 modes.
  symplectic basis: QuadPairBasis
mean: 4-element Vector{Float64}:
 2.0
 2.0
 0.0
 0.0
covariance: 4×4 Matrix{Float64}:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  5.0  0.0
 0.0  0.0  0.0  5.0
```
