```
RidgePred
```

Regularized predictor using ridge regression on the `p` features.

# Members

  * `X`: model matrix
  * `λ`: shrinkage parameter of the regularizer
  * `G`: regularizer matrix of size p×p.
  * `βprior`: regularizer prior of the coefficient values. Default to `zeros(p)`.
  * `pred`: the non-regularized predictor using an extended model matrix.
  * `pivot`: for `DensePredChol`, if the decomposition was pivoted.
  * `scratchbeta`: scratch vector of length `p`, used in [`GLM.linpred!`](@ref) method
