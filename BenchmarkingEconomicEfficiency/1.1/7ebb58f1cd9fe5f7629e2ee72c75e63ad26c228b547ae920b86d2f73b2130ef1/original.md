```
deaprofitadd(X, Y, W, P, model)
```

Compute profit efficiency using data envelopment analysis weighted additive model for inputs `X`, outputs `Y`, price of inputs `W`, and price of outputs `P`.

Model specification:

  * `:Ones`: standard additive DEA model.
  * `:MIP`: Measure of Inefficiency Proportions. (Charnes et al., 1987; Cooper et al., 1999)
  * `:Normalized`: Normalized weighted additive DEA model. (Lovell and Pastor, 1995)
  * `:RAM`: Range Adjusted Measure. (Cooper et al., 1999)
  * `:BAM`: Bounded Adjusted Measure. (Cooper et al, 2011)
  * `:Custom`: User supplied weights.

# Optional Arguments

  * `rhoX`: matrix of weights of inputs. Only if `model=:Custom`.
  * `rhoY`: matrix of weights of outputs. Only if `model=:Custom`.
  * `monetary=false`: decomposition in normalized terms. Monetary terms if `true`.
  * `names`: a vector of strings with the names of the decision making units.
