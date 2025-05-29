Hx = jth_hess(nlp, x, j)

Evaluate the Hessian of j-th constraint at `x` as a sparse matrix with the same sparsity pattern as the Lagrangian Hessian. A `Symmetric` object wrapping the lower triangle is returned.
