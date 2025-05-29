```julia
abstract type ThreeParameterLogisticModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

An abstract representation of a 3 Parameter Logistic Model with an item response function given by

$P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = c_j + (1 - c_j)\cdot\mathrm{logistic}(a_j(\theta_i - b_j))$

The item parameters `beta` must be a destructurable object with the following fields:

  * `a`: the item discrimination
  * `b`: the item difficulty (location)
  * `c`: the lower asymptote

**Alias:** `ThreePL`
