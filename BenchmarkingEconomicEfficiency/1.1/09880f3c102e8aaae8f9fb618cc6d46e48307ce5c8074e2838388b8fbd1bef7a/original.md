```
deaprofitgda(X, Y, W, P, measure)
```

Compute profit efficiency using data envelopment analysis General Direct Approach model for inputs `X`, outputs `Y`, price of inputs `W`, price of outputs `P`, and efficiency `measure`.

# Measure specification:

  * `:ERG`: Enhanced Russell Graph (or Slack Based Measure (SBM)).

# Optional Arguments

  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `atol=1e-6`: tolerance for DMU to be considered efficient.
  * `names`: a vector of strings with the names of the decision making units.
