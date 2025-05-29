```
FriedmanTest(x_1, x_2, ..., x_k; kwargs...) = FDistFriedmanTest(x_1, x_2, ..., x_k; kwargs...)
FriedmanTest(X; kwargs...) = FDistFriedmanTest(X; kwargs...)
```

Test the null hypothesis that `n` repeated observations of a set of `k` treatments    have the same distribution across all treatments. These observations are arranged    in `k` vectors `x_i` of `n` observations each or in an `(n, k)`-shaped matrix `X`.

The default version of this test, the `FDistFriedmanTest`, uses an F-distributed statistic.

**See also:** `FDistFriedmanTest`, `ChisqFriedmanTest`

# Keyword arguments

  * `maximize_outcome=false` specifies whether the ranks represent a maximization or a minimization of the outcomes.
