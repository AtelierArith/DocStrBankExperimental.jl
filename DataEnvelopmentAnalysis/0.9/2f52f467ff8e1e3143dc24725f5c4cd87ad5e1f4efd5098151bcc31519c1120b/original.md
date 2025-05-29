```
deaerg(X, Y)
```

Compute data envelopment analysis Enhanced Russell Graph Slack Based Measure for inputs `X` and outputs `Y`.

# Optional Arguments

  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `names`: a vector of strings with the names of the decision making units.
