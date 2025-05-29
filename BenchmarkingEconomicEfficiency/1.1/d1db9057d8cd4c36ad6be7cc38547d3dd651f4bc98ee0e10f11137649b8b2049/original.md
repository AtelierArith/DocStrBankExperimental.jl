```
deaprofitholder(X, Y, W, P; l)
```

Compute profit efficiency using data envelopment analysis Hölder model for inputs `X`, outputs `Y`, price of inputs `W`, and price of outputs `P`.

# Hölder norm `l` specification

  * `1`.
  * `2`.
  * `Inf`.

# Optional Arguments

  * `weigt=false`:  set to `true` for weighted (weakly) Hölder distance function.
  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `names`: a vector of strings with the names of the decision making units.
