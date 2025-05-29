```
deabigdata(X, Y)
```

Compute the big data radial model using data envelopment analysis for inputs X and outputs Y.

# Optional Arguments

  * `orient=:Input`: chooses the radially oriented input mode. For the radially oriented output model choose `:Output`.
  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `atol=1e-6`: tolerance for DMU to be considered efficient.
  * `names`: a vector of strings with the names of the decision making units.
