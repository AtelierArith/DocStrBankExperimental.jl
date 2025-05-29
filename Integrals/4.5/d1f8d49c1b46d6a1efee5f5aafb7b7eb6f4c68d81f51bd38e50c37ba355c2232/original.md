```
QuadratureRule(q; n=250)
```

Algorithm to construct and evaluate a quadrature rule `q` of `n` points computed from the inputs as `x, w = q(n)`. It assumes the nodes and weights are for the standard interval `[-1, 1]^d` in `d` dimensions, and rescales the nodes to the specific hypercube being solved. The nodes `x` may be scalars in 1d or vectors in arbitrary dimensions, and the weights `w` must be scalar. The algorithm computes the quadrature rule `sum(w .* f.(x))` and the caller must check that the result is converged with respect to `n`.
