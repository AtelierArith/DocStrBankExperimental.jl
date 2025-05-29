```
dea(X, Y)
```

Compute the radial model using data envelopment analysis for inputs X and outputs Y.

# Optional Arguments

  * `orient=:Input`: chooses the radially oriented input mode. For the radially oriented output model choose `:Output`.
  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `slack=true`: computes input and output slacks.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `disposX=:Strong`: chooses strong disposability of inputs. For weak disposability choose `:Weak`.
  * `disposY=:Strong`: chooses strong disposability of outputs. For weak disposability choose `:Weak`.
  * `names`: a vector of strings with the names of the decision making units.
