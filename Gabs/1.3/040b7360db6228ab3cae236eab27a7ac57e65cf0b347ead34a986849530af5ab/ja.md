```
changebasis(::SymplecticBasis, state::GaussianUnitary)
```

ガウスユニタリのシンプレクティック基底を変更します。

## 例

```jldoctest
julia> op = displace(QuadBlockBasis(2), 1.0-im)
GaussianUnitary for 2 modes.
  symplectic basis: QuadBlockBasis
displacement: 4-element Vector{Float64}:
  2.0
  2.0
 -2.0
 -2.0
symplectic: 4×4 Matrix{Float64}:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.0
 0.0  0.0  0.0  1.0

julia> changebasis(QuadPairBasis, op)
GaussianUnitary for 2 modes.
  symplectic basis: QuadPairBasis
displacement: 4-element Vector{Float64}:
  2.0
 -2.0
  2.0
 -2.0
symplectic: 4×4 Matrix{Float64}:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.0
 0.0  0.0  0.0  1.0
```
