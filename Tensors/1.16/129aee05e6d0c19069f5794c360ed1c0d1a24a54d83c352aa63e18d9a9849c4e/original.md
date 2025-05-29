```
dott(A::SecondOrderTensor)
```

Compute the dot-transpose product of `A` with itself, i.e. `dot(A, A')`. Return a `SymmetricTensor`.

# Examples

```jldoctest
julia> A = rand(Tensor{2,3})
3×3 Tensor{2, 3, Float64, 9}:
 0.325977  0.894245  0.953125
 0.549051  0.353112  0.795547
 0.218587  0.394255  0.49425

julia> dott(A)
3×3 SymmetricTensor{2, 3, Float64, 6}:
 1.81438   1.253    0.894897
 1.253     1.05904  0.65243
 0.894897  0.65243  0.4475
```
