```
vol(::SecondOrderTensor)
```

Computes the volumetric part of a second order tensor based on the additive decomposition.

# Examples

```jldoctest
julia> A = rand(SymmetricTensor{2,3})
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.325977  0.549051  0.218587
 0.549051  0.894245  0.353112
 0.218587  0.353112  0.394255

julia> vol(A)
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.538159  0.0       0.0
 0.0       0.538159  0.0
 0.0       0.0       0.538159

julia> vol(A) + dev(A) ≈ A
true
```
