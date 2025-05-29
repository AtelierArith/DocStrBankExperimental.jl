```
sparse_triangular_solve(U::CSR{F}, B::CSR{F}, k::Int, xj::Vector{Int32}, x::Vector{ZZp{F}}, qinv::Vector{Int32})
```

Solve x * U = B[k], where U is (permuted) triangular (either upper or lower).

x must have size m (#columns of U); it does not need to be initialized. xj must be preallocated of size 3*m and zero-initialized (it remains OK) qinv locates the pivots in U.

On output, the solution is scattered in x, and its pattern is given in xj[top:m]. The precise semantics is as follows. Define:          x*a = { j in [0:m] : qinv[j] < 0 }          x*b = { j in [0:m] : qinv[j] >= 0 } Then x*b * U + x*a == B[k].  It follows that x * U == y has a solution iff x_a is empty.

top is the return value

This does not require the pivots to be the first entry of the row. This requires that the pivots in U are all equal to 1.
