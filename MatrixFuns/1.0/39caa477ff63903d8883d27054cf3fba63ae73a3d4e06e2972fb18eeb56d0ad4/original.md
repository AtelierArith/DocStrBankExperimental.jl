```
mat_fun(f, A; sep, max_deg, scale, color, ε, checknative)
```

Compute the matrix-variable function `f(A)`. Return a matrix.

`f` a general scalar function, and called as `f(x)`.

`A` an arbitrary square matrix.

`sep` the initial separation distance, to split the eigenvalues of `A` into clusters that satisfy (i) min{|λ - μ|: λ ∈ cl*p, μ ∈ cl*q, p ≠ q} > sep.		 (ii) for cl*p with |cl*p| > 1, ∀ λ ∈ cl*p, ∃ μ ∈ cl*p and μ ≠ λ, s.t. |λ - μ| ≤ sep.  Here cl_p is the cluster with index p. When `sep=Inf`, the eigenvalues are only split by `color`.

`max_deg` the maximum Taylor series order for the diagonal blocks computation.

`tol_taylor` the termination tolerance for evaluating the Taylor series of diagonal blocks.

`scale` the scaling of the Talyor series error, is used to control the spread of each splitting cluster. When `scale=Inf`, split the eigenvalues only once with `sep`.

`color(x::Number)::Integer` an index mapping function.  This is to ensure all eigenvalues within a cluster have the same color index.  By default, the `color` function maps `x` to `1`.  For discontinuous functions, users can assign a distinct color to each continuous interval.  E.g., for the `sign` function, users can customize the color mapping using  `color = x -> Int(real(sign(x)))`

`ε` the default error.

`ε_im` the default error for the imaginary part of f(A) (used for complex Schur decomposition).

`checknative` check `f` is a Julia native function.
