```
basis_transform(A, B)
```

Compute the (possibly dense) basis transform matrix to go from `B` to `A`, via [`basis_overlap`](@ref) for non-orthogonal basis `A`:

$$
(B^HB)^{-1}B^HA
$$
