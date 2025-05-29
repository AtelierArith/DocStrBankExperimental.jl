```
W = Woodbury(A, U, C, V; allocatetmp::Bool=false)
```

Represent a matrix `W = A + UCV`. Equations `Wx = b` will be solved using the [Woodbury matrix identity](https://en.wikipedia.org/wiki/Woodbury_matrix_identity).

If your main goal is to solve equations, it's often advantageous to supply `A` as a factorization (e.g., `Woodbury(lu(A), U, C, V)`).

If `allocatetmp` is true, temporary storage used for intermediate steps in multiplication and division will be allocated.

!!! warning
    If you'll use the same `W` in multiple threads, you should use `allocatetmp=false` or risk data races.


See also [SymWoodbury](@ref).
