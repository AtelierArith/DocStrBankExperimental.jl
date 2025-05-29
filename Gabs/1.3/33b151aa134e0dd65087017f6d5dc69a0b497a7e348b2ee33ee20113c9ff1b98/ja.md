```
changebasis(::SymplecticBasis, state::GaussianChannel)
```

ガウスチャネルのシンプレクティック基底を変更します。

# 例

```jldoctest
julia> ch = attenuator(QuadBlockBasis(2), [1.0, 2.0], [2, 4])
GaussianChannel for 2 modes.
  symplectic basis: QuadBlockBasis
displacement: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
transform: 4×4 Matrix{Float64}:
 0.540302   0.0       0.0        0.0
 0.0       -0.416147  0.0        0.0
 0.0        0.0       0.540302   0.0
 0.0        0.0       0.0       -0.416147
noise: 4×4 Matrix{Float64}:
 1.41615  0.0      0.0      0.0
 0.0      3.30729  0.0      0.0
 0.0      0.0      1.41615  0.0
 0.0      0.0      0.0      3.30729

julia> changebasis(QuadPairBasis, ch)
GaussianChannel for 2 modes.
  symplectic basis: QuadPairBasis
displacement: 4-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
transform: 4×4 Matrix{Float64}:
 0.540302  0.0        0.0        0.0
 0.0       0.540302   0.0        0.0
 0.0       0.0       -0.416147   0.0
 0.0       0.0        0.0       -0.416147
noise: 4×4 Matrix{Float64}:
 1.41615  0.0      0.0      0.0
 0.0      1.41615  0.0      0.0
 0.0      0.0      3.30729  0.0
 0.0      0.0      0.0      3.30729
```
