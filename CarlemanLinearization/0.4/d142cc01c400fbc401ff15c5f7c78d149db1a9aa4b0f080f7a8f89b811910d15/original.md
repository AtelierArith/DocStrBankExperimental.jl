```
kron_sum(F::AbstractMatrix, k::Int)
```

Compute the Kronecker sum of order k defined as:

$$
    F ⊕ F ⊕ ... ⊕ F := F ⊗ I ⊗ ... ⊗ I + I ⊗ F ⊗ I ⊗ ... ⊗ I + ... + I ⊗ ... ⊗ I ⊗ F
$$

where each term has `k` products and there are a total of `k` summands and `I` is the identity matrix of order `n`.

### Examples

It holds that:

  * $k = 1: F$
  * $k = 2: F ⊗ I + I ⊗ F$
  * $k = 3: F ⊗ I ⊗ I + I ⊗ F ⊗ I + I ⊗ I ⊗ F$

```jldoctest
julia> F = sparse([0 1; -1 0.])
2×2 SparseMatrixCSC{Float64,Int64} with 2 stored entries:
  [2, 1]  =  -1.0
  [1, 2]  =  1.0

julia> kron_sum(F, 1) == F
true

julia> I2 = I(2)
IdentityMultiple{Float64} of value 1.0 and order 2

julia> kron_sum(F, 2) == kron(F, I2) + kron(I2, F)
true

julia> kron_sum(F, 3) == sum(reduce(kron, X) for X in [[F, I2, I2], [I2, F, I2], [I2, I2, F]])
true
```
