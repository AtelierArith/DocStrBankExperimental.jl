```
AffineConstraint(constrained_dof::Int, entries::Vector{Pair{Int,T}}, b::T) where T
```

1つの自由度 `u[i]` を制約するアフィン/線形制約を定義します。ここで、`u[i] = ∑(u[j] * a[j]) + b` となり、`i=constrained_dof` であり、`entries` の各要素は `j => a[j]` です。
