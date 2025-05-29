```
malmquist(X, Y)
```

Compute the Malmquist productivity index using data envelopment analysis for inputs `X` and outputs `Y`.

# Optional Arguments

  * `orient=:Input`: chooses between input oriented radial model `:Input` or output oriented radial model `:Output`.
  * `refperiod=:Geomean`: chooses reference period for technological change: `:Base`, `:Comparison` or `:Geomean`.
  * `rts=:CRS`: chooses constant returns to scale. For variable returns to scale choose `:VRS`.
  * `names`: a vector of strings with the names of the decision making units.
