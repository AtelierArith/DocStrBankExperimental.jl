```
dot(::SymmetricTensor{2})
```

Compute the dot product of a symmetric second order tensor with itself. Return a `SymmetricTensor`.

See also [`tdot`](@ref) and [`dott`](@ref).

# Examples

```jldoctest
julia> A = rand(SymmetricTensor{2,3})
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.325977  0.549051  0.218587
 0.549051  0.894245  0.353112
 0.218587  0.353112  0.394255

julia> dot(A)
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.455498  0.74715  0.351309
 0.74715   1.22582  0.575
 0.351309  0.575    0.327905
```
