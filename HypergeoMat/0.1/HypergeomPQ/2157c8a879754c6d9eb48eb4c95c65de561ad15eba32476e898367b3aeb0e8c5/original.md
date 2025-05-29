```
hypergeomPQ(m, a, b, x[, alpha])
```

Compute the truncated hypergeometric function of a matrix argument given the    eigen values of the matrix.

# Arguments

  * `m`: truncation weight of the summation, a positive integer
  * `a`: the "upper" parameters, a real or complex vector, possibly empty
  * `b`: the "lower" parameters, a real or complex vector, possibly empty
  * `x`: real or complex vector, the eigen values
  * `alpha`: the alpha parameter, a positive number; if missing, `alpha=2` is used
