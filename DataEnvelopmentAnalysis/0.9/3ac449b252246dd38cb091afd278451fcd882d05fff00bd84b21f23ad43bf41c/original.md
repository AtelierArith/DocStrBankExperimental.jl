```
dearddf(X, Y, measure)
```

Compute data envelopment analysis reverse directional distance function (RDDF) model for inputs `X`, outputs `Y`, and efficiency measure  `measure`.

# Measure specification:

  * `:ERG`: Enhanced Russell Graph (or Slack Based Measure (SBM)).
  * `:MDDF`: Modified Directional Distance Function.

# Direction specification:

For the Modified Directional Distance Function, the directions `Gx` and `Gy` can be one of the following symbols.

  * `:Ones`: use ones.
  * `:Observed`: use observed values.
  * `:Mean`: use column means.

# Optional Arguments

  * `orient=:Graph`: choose between graph oriented `:Graph`, input oriented `:Input`, or output oriented model `:Output`.
  * `rts=:CRS`: choose between constant returns to scale `:CRS` or variable returns to scale `:VRS`.
  * `atol=1e-6`: tolerance for DMU to be considered efficient.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `names`: a vector of strings with the names of the decision making units.
