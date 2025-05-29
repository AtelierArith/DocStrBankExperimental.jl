```
gradient(f, x)
gradient(f, x, :all)
```

Compute the gradient of `f` with respect to `x` by the automatic differentiation. If pseudo keyword `:all` is given, the value of `f(x)` is also returned.

# Examples

```jldoctest
julia> x = rand(Mat{3,3})
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.325977  0.894245  0.953125
 0.549051  0.353112  0.795547
 0.218587  0.394255  0.49425

julia> gradient(tr, x)
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> ∇f, f = gradient(tr, x, :all)
([1.0 0.0 0.0; 0.0 1.0 0.0; 0.0 0.0 1.0], 1.1733382401532275)
```
