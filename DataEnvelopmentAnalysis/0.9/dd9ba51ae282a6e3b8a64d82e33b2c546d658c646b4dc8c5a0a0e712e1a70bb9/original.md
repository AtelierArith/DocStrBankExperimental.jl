```
deaprofit(X, Y, W, P; Gx, Gy)
```

Compute profit efficiency using data envelopment analysis model for inputs `X`, outputs `Y`, price of inputs `W`, and price of outputs `P`.

# Direction specification:

The directions `Gx` and `Gy` can be one of the following symbols.

  * `:Zeros`: use zeros.
  * `:Ones`: use ones.
  * `:Observed`: use observed values.
  * `:Mean`: use column means.
  * `:Monetary`: use direction so that profit inefficiency is expressed in monetary values.

Alternatively, a vector or matrix with the desired directions can be supplied.

# Optional Arguments

  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `names`: a vector of strings with the names of the decision making units.
