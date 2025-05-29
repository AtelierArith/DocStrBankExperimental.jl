```
deagdf(X, Y, alpha)
```

Compute generalized distance function data envelopment analysis model for inputs `X`, outputs `Y`, and `alpha`.

# Optional Arguments

  * `alpha=0.5`: alpha value.
  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `slack=true`: compute input and output slacks.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `names`: a vector of strings with the names of the decision making units.
