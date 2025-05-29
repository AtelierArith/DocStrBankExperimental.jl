```
hypergeom_e(a, b, x::Float64) -> gsl_sf_result
```

Computes the appropriate hypergeometric ${}_p F_q$ function,  where $p$ and $p$ are the lengths of the input vectors `a` and `b` respectively.  

Singleton `a` and/or `b` may be specified as scalars,  and length-0 `a` and/or `b` may be input as simply `[]`.

Supported values of $(p, q)$ are $(0, 0)$, $(0, 1)$, $(1, 1)$, $(2, 0)$ and $(2, 1)$.
