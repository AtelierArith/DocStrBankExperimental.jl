```
vtnorm(A::AbstractArray, p::Real=2; dims=:)
```

Compute the `p`-norm of `A` along the dimensions `dims` as if the corresponding slices were vectors. Threaded.

`p` can assume any numeric value (even though not all values produce a mathematically valid vector norm). `vtnorm(A, Inf)` returns the largest value in `abs.(A)`, whereas `vtnorm(A, -Inf)` returns the smallest; `vnorm(A, 0)` matches the behavior of `LinearAlgebra.norm(A, 0)`.

See also: [`vnorm`](@ref)
