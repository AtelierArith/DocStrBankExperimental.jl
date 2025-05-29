```
dearussell(X, Y)
```

Compute the Russell model using data envelopment analysis for inputs X and outputs Y.

# Optional Arguments

  * `orient=:Input`: chooses the Russell input mode. For the Russell output model choose `:Output`. For the Russell graph model choose `:Graph`.
  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `slack=true`: computes input and output slacks.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `names`: a vector of strings with the names of the decision making units.
