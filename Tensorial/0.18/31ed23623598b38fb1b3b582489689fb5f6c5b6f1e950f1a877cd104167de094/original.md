```
rotate(x, R::SecondOrderTensor)
```

Rotate `x` using the rotation matrix `R`. This function preserves the symmetry of the matrix.

# Examples

```jldoctest
julia> R = rotmatz(π/4)
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.707107  -0.707107  0.0
 0.707107   0.707107  0.0
 0.0        0.0       1.0

julia> rotate(Vec(1,0,0), R)
3-element Vec{3, Float64}:
 0.7071067811865476
 0.7071067811865475
 0.0

julia> A = rand(SymmetricSecondOrderTensor{3})
3×3 SymmetricSecondOrderTensor{3, Float64, 6}:
 0.325977  0.549051  0.218587
 0.549051  0.894245  0.353112
 0.218587  0.353112  0.394255

julia> rotate(A, R) ≈ R * A * R'
true
```
