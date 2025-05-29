```
FDistFriedmanTest(x_1, x_2, ..., x_k; kwargs...)
FDistFriedmanTest(X; kwargs...)
```

Test the null hypothesis that `n` repeated observations of a set of `k` treatments    have the same distribution across all treatments. These observations are arranged    in `k` vectors `x_i` of `n` observations each or in an `(n, k)`-shaped matrix `X`.

This version of the `FriedmanTest` uses an F-distributed statistic.

# Keyword arguments

  * `maximize_outcome=false` specifies whether the ranks represent a maximization or a minimization of the outcomes.
