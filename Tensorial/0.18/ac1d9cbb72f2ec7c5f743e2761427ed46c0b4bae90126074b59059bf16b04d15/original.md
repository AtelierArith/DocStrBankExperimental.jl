```
minorsymmetric(::AbstractFourthOrderTensor) -> SymmetricFourthOrderTensor
```

Compute the minor symmetric part of a fourth order tensor.

# Examples

```jldoctest
julia> x = rand(Tensor{Tuple{3,3,3,3}});

julia> minorsymmetric(x) ≈ @einsum (i,j,k,l) -> (x[i,j,k,l] + x[j,i,k,l] + x[i,j,l,k] + x[j,i,l,k]) / 4
true
```
