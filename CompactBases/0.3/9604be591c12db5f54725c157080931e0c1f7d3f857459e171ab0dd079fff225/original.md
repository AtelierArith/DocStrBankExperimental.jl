```
basis_transform(A, B)
```

Compute the (possibly dense) basis transform matrix to go from `B` to `A`, via [`basis_overlap`](@ref), dispatching on the [`orthogonality`](@ref) trait of `A`.
