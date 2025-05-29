```
isgaussian(x::GaussianState)
isgaussian(x::GaussianUnitary)
isgaussian(x::GaussianChannel)
```

Check if `x` satisfies the corresponding Gaussian definition for its type.

## Example

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
