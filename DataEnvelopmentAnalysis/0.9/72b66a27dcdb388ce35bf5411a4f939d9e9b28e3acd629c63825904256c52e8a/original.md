```
deaaddweights(X, Y, model)
```

Compute corresponding weights for related data envelopment analysis weighted additive models for inputs `X` and outputs `Y`.

Model specification:

  * `:Ones`: standard additive DEA model.
  * `:MIP`: Measure of Inefficiency Proportions. (Charnes et al., 1987; Cooper et al., 1999)
  * `:Normalized`: Normalized weighted additive DEA model. (Lovell and Pastor, 1995)
  * `:RAM`: Range Adjusted Measure. (Cooper et al., 1999)
  * `:BAM`: Bounded Adjusted Measure. (Cooper et al, 2011)

# Optional Arguments

  * `orient=:Graph`: choose between graph oriented `:Graph`, input oriented `:Input`, or output oriented model `:Output`.
