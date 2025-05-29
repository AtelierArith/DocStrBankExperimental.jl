```
dearevenueddf(X, Y, P; Gy)
```

Compute revenue efficiency using directional distance function data envelopment analysis for inputs `X`, outputs `Y` and price of outputs `P`.

# Direction specification:

The direction `Gy` can be one of the following symbols.

  * `:Ones`: use ones.
  * `:Observed`: use observed values.
  * `:Mean`: use column means.
  * `:Monetary`: use direction so that profit inefficiency is expressed in monetary values.

Alternatively, a vector or matrix with the desired directions can be supplied.

# Optional Arguments

  * `rts=:VRS`: chooses variable returns to scale. For constant returns to scale choose `:CRS`.
  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `names`: a vector of strings with the names of the decision making units.
