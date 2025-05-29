```
deg_num_leading_terms(p::AbstractPolynomialLike, var)
```

Return `deg, num` where `deg = maxdegree(p, var)` and `num` is the number of terms `t` such that `degree(t, var) == deg`.
