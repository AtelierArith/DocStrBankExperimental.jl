```
dearevenueadd(X, Y, P, model)
```

Compute revenue efficiency using additive data envelopment analysis for inputs `X`, outputs `Y` and price of outputs `P`.

Model specification:

  * `:Ones`: standard additive DEA model.
  * `:MIP`: Measure of Inefficiency Proportions. (Charnes et al., 1987; Cooper et al., 1999)
  * `:Normalized`: Normalized weighted additive DEA model. (Lovell and Pastor, 1995)
  * `:RAM`: Range Adjusted Measure. (Cooper et al., 1999)
  * `:BAM`: Bounded Adjusted Measure. (Cooper et al, 2011)
  * `:Custom`: User supplied weights.

# Optional Arguments

  * `rts=:VRS`: chooses variable returns to scale. For constant returns to scale choose `:CRS`.
  * `rhoY`: matrix of weights of outputs. Only if `model=:Custom`.
  * `disposal=:Strong`: chooses strong disposal of inputs. For weak disposal choose `:Weak`.
  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `names`: a vector of strings with the names of the decision making units.
