```
deaadd(X, Y, model)
```

Compute related data envelopment analysis weighted additive models for inputs `X` and outputs `Y`.

Model specification:

  * `:Ones`: standard additive DEA model.
  * `:MIP`: Measure of Inefficiency Proportions. (Charnes et al., 1987; Cooper et al., 1999)
  * `:Normalized`: Normalized weighted additive DEA model. (Lovell and Pastor, 1995)
  * `:RAM`: Range Adjusted Measure. (Cooper et al., 1999)
  * `:BAM`: Bounded Adjusted Measure. (Cooper et al, 2011)
  * `:Custom`: User supplied weights.

# Optional Arguments

  * `orient=:Graph`: choose between graph oriented `:Graph`, input oriented `:Input`, or output oriented model `:Output`.
  * `rts=:VRS`: choose between constant returns to scale `:CRS` or variable returns to scale `:VRS`.
  * `rhoX`: matrix of weights of inputs. Only if `model=:Custom`.
  * `rhoY`: matrix of weights of outputs. Only if `model=:Custom`.
  * `Xref=X`: Identifies the reference set of inputs against which the units are evaluated.
  * `Yref=Y`: Identifies the reference set of outputs against which the units are evaluated.
  * `disposX=:Strong`: chooses strong disposability of inputs. For weak disposability choose `:Weak`.
  * `disposY=:Strong`: chooses strong disposability of outputs. For weak disposability choose `:Weak`.
  * `names`: a vector of strings with the names of the decision making units.
