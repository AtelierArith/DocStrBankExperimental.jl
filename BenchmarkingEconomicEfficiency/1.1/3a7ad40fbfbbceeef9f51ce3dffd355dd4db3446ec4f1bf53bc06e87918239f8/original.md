```
deaprofitrddf(X, Y, W, P, measure)
```

Compute profit efficiency using data envelopment analysis Reverse DDF model for inputs `X`, outputs `Y`, price of inputs `W`, price of outputs `P`, and efficiency `measure`.

# Measure specification:

  * `:ERG`: Enhanced Russell Graph Slack Based Measure.
  * `:MDDF`: Modified Directional Distance Function.

# Direction specification:

For the Modified Directional Distance Function, the directions `Gx` and `Gy` can be one of the following symbols.

  * `:Observed`: use observed values.

Alternatively, a vector or matrix with the desired directions can be supplied.

# Optional Arguments

  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `atol=1e-6`: tolerance for DMU to be considered efficient.
  * `names`: a vector of strings with the names of the decision making units.
