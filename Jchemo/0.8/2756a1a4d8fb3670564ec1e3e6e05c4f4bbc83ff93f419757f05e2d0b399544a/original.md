```
coef(object::Union{Plsr, Pcr, Splsr}; nlv = nothing)
```

Compute the b-coefficients of a LV model.

  * `object` : The fitted model.
  * `nlv` : Nb. LVs to consider.

For a model fitted from X(n, p) and Y(n, q), the returned  object `B` is a matrix (p, q). If `nlv` = 0, `B` is a matrix  of zeros. The returned object `int` is the intercept.
