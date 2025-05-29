```
kron_id(n, k)
```

Compute the k-fold Kronecker product of the identity: `I ⊗ I ⊗ ... ⊗ I`, k times.

### Input

  * `n` – integer representing the order (dimension of the identity)
  * `k` – integer representing the power

### Output

An identity matrix of order $n^k$ and type `Diagonal`.

### Examples

```jldoctest
julia> kron_id(2, 2)
4×4 Diagonal{Float64,Array{Float64,1}}:
 1.0   ⋅    ⋅    ⋅
  ⋅   1.0   ⋅    ⋅
  ⋅    ⋅   1.0   ⋅
  ⋅    ⋅    ⋅   1.0
```
