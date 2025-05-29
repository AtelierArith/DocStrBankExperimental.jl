```
vol(A)
```

Compute the volumetric part of a square tensor `A`. This is only available in 3D.

# Examples

```jldoctest
julia> x = rand(Mat{3,3})
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.325977  0.894245  0.953125
 0.549051  0.353112  0.795547
 0.218587  0.394255  0.49425

julia> vol(x)
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.391113  0.0       0.0
 0.0       0.391113  0.0
 0.0       0.0       0.391113

julia> vol(x) + dev(x) ≈ x
true
```
