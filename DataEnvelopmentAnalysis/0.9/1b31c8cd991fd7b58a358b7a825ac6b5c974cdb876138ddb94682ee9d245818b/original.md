```
deam(X, Y)
```

Compute the radial multiplier model using data envelopment analysis for inputs X and outputs Y.

# Optional Arguments

  * `orient=:Input`: chooses the radially oriented input mode. For the radially oriented output model choose `:Output`.
  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `names`: a vector of strings with the names of the decision making units.
