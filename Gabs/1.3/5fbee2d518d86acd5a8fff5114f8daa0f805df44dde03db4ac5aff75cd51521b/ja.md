```
isgaussian(x::GaussianState)
isgaussian(x::GaussianUnitary)
isgaussian(x::GaussianChannel)
```

`x`がその型に対応するガウス定義を満たしているかどうかを確認します。

## 例

```jldoctest
julia> basis = QuadPairBasis(1);

julia> op = displace(basis, 1.0-im)
GaussianUnitary for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 2.0
 -2.0
symplectic: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

julia> isgaussian(op)
true
```
