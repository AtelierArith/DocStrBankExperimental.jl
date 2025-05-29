```
X = nonneg_lsq(A, B; gram=false, alg=:pivot, variant=:none, use_parallel=true, kwargs...)
X = nonneg_lsq(A'*A, A'*B; gram=true, ...)
```

Computes the matrix `X` that minimizes `vecnorm(A*X - B)` subject to `X .>= 0`, where `A` is an (m-by-k) matrix and `B` is a (m-by-n) matrix. Alternatively one can supply a vector `b`.

## Optional arguments

`alg`: a symbol specifying the algorithm to be used

  * `:pivot`: Block-pivoting active-set-like method (Kim & Park, 2011)
  * `:fnnls`: Fast active-set method (Bro & De Jong, 1997)
  * `:nnls`: Classic active-set method (Lawson & Hanson, 1974)
  * `:admm`: Alternating Direction Method of Multipliers (e.g., Boyd et al., 2011)

`variant`: a symbol specifying the variant (applicable only to `alg=:pivot`, with potential values `:comb` or `:cache`)

`gram`: a boolean that should be set to `true` if one is supplying Gram matrices `A'*A`,`A'*B` instead of the data matrices `A`,`B`.

`tol:` tolerance for nonnegativity constraints

`max_iter:` maximum number of iterations before function gives up

`use_parallel`: use threading if `B` has multiple columns and `Threads.nthreads() > 1`.
