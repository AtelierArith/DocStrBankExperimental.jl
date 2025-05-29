```
kron_sandwich(F, n, k1, k2)
```

Compute `A ⊗ F ⊗ C` where `A = I^{⊗ k1}` and `C = I^{⊗ k2}` where `I` is the identity matrix of order `n`, the `k1`-fold and `k2`-fold Kronecker product of the identity and `F` in between.

### Input

  * `F`  – matrix
  * `n`  – integer, dimension of the identity
  * `k1` – nonnegative integer
  * `k2` – nonnegative integer

### Output

The kronecker product `I^{⊗ k1} ⊗ F ⊗ I^{⊗ k2}`, represented as a sparse matrix if `F` is sparse.

### Examples

```jldoctest
julia> F = sparse([0 1; -1 0.])
2×2 SparseMatrixCSC{Float64,Int64} with 2 stored entries:
  [2, 1]  =  -1.0
  [1, 2]  =  1.0

julia> Q = kron_sandwich(F, 2, 2, 2);

julia> size(Q)
(32, 32)

julia> I2 = I(2)
IdentityMultiple{Float64} of value 1.0 and order 2

julia> Q == reduce(kron, [I2, I2, F, I2, I2])
true
```
