```
SymmetricTensor{order,dim,T<:Number}
```

`order ∈ (2,4)` および `dim ∈ (1,2,3)` に対応する対称テンソル型。`SymmetricTensor{4}` は小さな対称テンソルであり、`A[i,j,k,l] == A[j,i,k,l]` および `A[i,j,k,l] == A[i,j,l,k]` が成り立ちます。

# 例

```jldoctest
julia> SymmetricTensor{2,2,Float64}((1.0, 2.0, 3.0))
2×2 SymmetricTensor{2, 2, Float64, 3}:
 1.0  2.0
 2.0  3.0
```
