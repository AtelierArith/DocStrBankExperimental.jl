```
deaboot(X, Y)
```

Compute the bootstrap radial model using data envelopment analysis for inputs X and outputs Y.

# Optional Arguments

  * `nreps=200`: number of bootstrap replications.
  * `rng=default_rng()`: random number generator.
  * `orient=:Input`: chooses the radially oriented input mode. For the radially oriented output model choose `:Output`.
  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `disposX=:Strong`: chooses strong disposability of inputs. For weak disposability choose `:Weak`.
  * `disposY=:Strong`: chooses strong disposability of outputs. For weak disposability choose `:Weak`.
  * `names`: a vector of strings with the names of the decision making units.
