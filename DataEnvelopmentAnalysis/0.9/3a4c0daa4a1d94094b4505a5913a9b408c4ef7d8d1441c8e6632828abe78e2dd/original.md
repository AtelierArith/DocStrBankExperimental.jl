```
deamddf(X, Y; Gx, Gy)
```

Compute data envelopment analysis modified directional distance function model for inputs `X` and outputs `Y`, using directions `Gx` and `Gy`.

# Direction specification:

The directions `Gx` and `Gy` can be one of the following symbols.

  * `:Ones`: use ones.
  * `:Observed`: use observed values.
  * `:Mean`: use column means.

Alternatively, a vector or matrix with the desired directions can be supplied.

# Optional Arguments

  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `slack=true`: computes input and output slacks.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `names`: a vector of strings with the names of the decision making units.
