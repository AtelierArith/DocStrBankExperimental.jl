```
tensor(A, B)
A ⊗ B
```

Compute the tensor product of `A` and `B`. If `C = A ⊗ B`, then `C[i1, ..., im, j1, ..., jn] = A[i1, ... im] * B[j1, ..., jn]`.

For vectors `v` and `w`, the Kronecker product is related to the tensor product by `kron(v,w) == vec(w ⊗ v)` or `w ⊗ v == reshape(kron(v,w), (length(w), length(v)))`.

# Examples

```jldoctest; setup=:(using TensorCore)
julia> a = [2, 3]; b = [5, 7, 11];

julia> a ⊗ b
2×3 Array{Int64,2}:
 10  14  22
 15  21  33
```

See also `tensor!(Y,A,B)`.
