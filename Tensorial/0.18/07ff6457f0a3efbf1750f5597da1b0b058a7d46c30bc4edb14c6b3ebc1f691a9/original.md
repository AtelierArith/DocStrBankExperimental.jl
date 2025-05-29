```
symmetric(::AbstractSecondOrderTensor)
symmetric(::AbstractSecondOrderTensor, uplo)
```

Compute the symmetric part of a second order tensor.

# Examples

```jldoctest
julia> x = rand(Mat{3,3})
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.325977  0.894245  0.953125
 0.549051  0.353112  0.795547
 0.218587  0.394255  0.49425

julia> symmetric(x)
3×3 SymmetricSecondOrderTensor{3, Float64, 6}:
 0.325977  0.721648  0.585856
 0.721648  0.353112  0.594901
 0.585856  0.594901  0.49425

julia> symmetric(x, :U)
3×3 SymmetricSecondOrderTensor{3, Float64, 6}:
 0.325977  0.894245  0.953125
 0.894245  0.353112  0.795547
 0.953125  0.795547  0.49425
```
