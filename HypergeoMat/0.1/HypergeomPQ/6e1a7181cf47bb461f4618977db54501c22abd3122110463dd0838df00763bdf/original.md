```
hypergeomPQ(m, a, b, X[, alpha])
```

Compute the truncated hypergeometric function of a matrix argument. The    hypergeometric function is usually defined for a symmetric real matrix     or a Hermitian complex matrix but arbitrary square matrices are allowed.

# Arguments

  * `m`: truncation weight of the summation, a positive integer
  * `a`: the "upper" parameters, a real or complex vector, possibly empty
  * `b`: the "lower" parameters, a real or complex vector, possibly empty
  * `X`: a square matrix, real or complex
  * `alpha`: the alpha parameter, a positive number; if missing, `alpha=2` is used
