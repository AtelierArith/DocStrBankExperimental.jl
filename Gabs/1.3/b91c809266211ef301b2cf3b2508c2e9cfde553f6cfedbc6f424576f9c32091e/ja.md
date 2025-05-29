```
ptrace([Tm=Vector{Float64}, Tc=Matrix{Float64},] state::GaussianState, idx<:Int)
ptrace([Tm=Vector{Float64}, Tc=Matrix{Float64},] state::GaussianState, indices<:AbstractVector)
```

部分トレースは、`idx` で示されるサブシステムまたは `indices` で示される複数のサブシステムに対するガウス状態のものです。

## 例

```jldoctest
julia> basis = QuadPairBasis(1);

julia> state = coherentstate(basis, 1.0+im) ⊗ thermalstate(basis, 2) ⊗ squeezedstate(basis, 3.0, pi/4);

julia> ptrace(state, 2)
GaussianState for 2 modes.
  symplectic basis: QuadPairBasis
mean: 4-element Vector{Float64}:
 2.0
 2.0
 0.0
 0.0
covariance: 4×4 Matrix{Float64}:
 1.0  0.0     0.0        0.0
 0.0  1.0     0.0        0.0
 0.0  0.0    59.0829  -142.633
 0.0  0.0  -142.633    344.348

julia> ptrace(state, [1, 3])
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 0.0
 0.0
covariance: 2×2 Matrix{Float64}:
 5.0  0.0
 0.0  5.0
```
