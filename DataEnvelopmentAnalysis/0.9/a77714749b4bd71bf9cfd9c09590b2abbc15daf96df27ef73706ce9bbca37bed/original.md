```
deacost(X, Y, W)
```

Compute cost efficiency using data envelopment analysis for inputs `X`, outputs `Y` and price of inputs `W`.

# Optional Arguments

  * `rts=:VRS`: chooses variable returns to scale. For constant returns to scale choose `:CRS`.
  * `dispos=:Strong`: chooses strong disposability of outputs. For weak disposability choose `:Weak`.
  * `names`: a vector of strings with the names of the decision making units.
