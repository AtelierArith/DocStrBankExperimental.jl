```
SymmetricTensor{order,dim,T<:Number}
```

Symmetric tensor type supported for `order ∈ (2,4)` and `dim ∈ (1,2,3)`. `SymmetricTensor{4}` is a minor symmetric tensor, such that `A[i,j,k,l] == A[j,i,k,l]` and `A[i,j,k,l] == A[i,j,l,k]`.

# Examples

```jldoctest
julia> SymmetricTensor{2,2,Float64}((1.0, 2.0, 3.0))
2×2 SymmetricTensor{2, 2, Float64, 3}:
 1.0  2.0
 2.0  3.0
```
