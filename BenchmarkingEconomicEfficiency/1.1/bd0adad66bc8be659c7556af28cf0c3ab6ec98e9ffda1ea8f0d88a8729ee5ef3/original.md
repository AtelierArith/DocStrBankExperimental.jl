```
dearevenuerddf(X, Y, P, measure)
```

Compute profit efficiency using data envelopment analysis Reverse DDF model for inputs `X`, outputs `Y`, price of outputs `P`, and efficiency `measure`.

# Measure specification:

  * `:ERG`: Enhanced Russell Graph Slack Based Measure.

# Optional Arguments

  * `rts=:VRS`: choose between constant returns to scale `:CRS` or variable returns to scale `:VRS`.
  * `atol=1e-6`: tolerance for DMU to be considered efficient.
  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `names`: a vector of strings with the names of the decision making units.
