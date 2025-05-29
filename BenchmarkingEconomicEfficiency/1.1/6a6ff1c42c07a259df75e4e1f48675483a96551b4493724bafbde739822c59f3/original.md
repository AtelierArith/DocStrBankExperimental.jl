```
dearevenuegda(X, Y, P, measure)
```

Compute revenue efficiency using data envelopment analysis General Direct Approach model for inputs `X`, outputs `Y`, price of outputs `P`, and efficiency `measure`.

# Measure specification:

  * `:ERG`: Enhanced Russell Graph (or Slack Based Measure (SBM)).

# Optional Arguments

  * `rts=:VRS`: choose between constant returns to scale `:CRS` or variable returns to scale `:VRS`.
  * `atol=1e-6`: tolerance for DMU to be considered efficient.
  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `names`: a vector of strings with the names of the decision making units.
