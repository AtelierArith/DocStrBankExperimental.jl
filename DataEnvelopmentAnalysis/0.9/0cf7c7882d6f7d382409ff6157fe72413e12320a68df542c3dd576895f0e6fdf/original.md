```
dearevenue(X, Y, P)
```

Compute revenue efficiency using data envelopment analysis for inputs `X`, outputs `Y` and price of outputs `P`.

# Optional Arguments

  * `rts=:VRS`: chooses variable returns to scale. For constant returns to scale choose `:CRS`.
  * `dispos=:Strong`: chooses strong disposability of inputs. For weak disposability choose `:Weak`.
  * `names`: a vector of strings with the names of the decision making units.
