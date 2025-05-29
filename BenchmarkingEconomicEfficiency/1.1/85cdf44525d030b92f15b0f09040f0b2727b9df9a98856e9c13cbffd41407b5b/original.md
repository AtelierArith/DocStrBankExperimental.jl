```
deacostholder(X, Y, W; l)
```

Compute cost efficiency using data envelopment analysis for inputs `X`, outputs `Y` and price of inputs `W`.

# Hölder norm `l` specification

  * `1`.
  * `2`.
  * `Inf`.

# Optional Arguments

  * `weigt=false`:  set to `true` for weighted (weakly) Hölder distance function.
  * `rts=:VRS`: chooses variable returns to scale. For constant returns to scale choose `:CRS`.
  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `names`: a vector of strings with the names of the decision making units.
