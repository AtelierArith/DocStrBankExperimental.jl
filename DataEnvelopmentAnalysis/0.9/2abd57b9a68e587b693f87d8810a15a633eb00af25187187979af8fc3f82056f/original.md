```
deaholder(X, Y; l)
```

Compute the Hölder distance function model using data envelopment analysis for inputs `X` and outputs `Y`,  using Hölder norm `l`.

# Hölder norm `l` specification

  * `1`.
  * `2`.
  * `Inf`.

# Optional Arguments

  * `weigt=false`:  set to `true` for weighted (weakly) Hölder distance function.
  * `orient=:Input`: chooses the radially oriented input mode. For the radially oriented output model choose `:Output`.
  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `slack=true`: computes input and output slacks.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `names`: a vector of strings with the names of the decision making units.
