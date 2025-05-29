```
transpose(::Vec)
transpose(::SecondOrderTensor)
transpose(::FourthOrderTensor)
```

Compute the transpose of a tensor. For a fourth order tensor, the transpose is the minor transpose.

# Examples

```jldoctest
julia> A = rand(Tensor{2,2})
2×2 Tensor{2, 2, Float64, 4}:
 0.325977  0.218587
 0.549051  0.894245

julia> A'
2×2 Tensor{2, 2, Float64, 4}:
 0.325977  0.549051
 0.218587  0.894245
```
