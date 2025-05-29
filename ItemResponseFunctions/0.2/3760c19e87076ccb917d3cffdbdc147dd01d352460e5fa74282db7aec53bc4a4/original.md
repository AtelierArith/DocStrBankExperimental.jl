```julia
abstract type TwoParameterLogisticModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

An abstract representation of a 2 Parameter Logistic Model with an item response function given by

$P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = \mathrm{logistic}(a_j(\theta_i - b_j))$

The item parameters `beta` must be a destructurable object with the following fields:

  * `a`: the item discrimination
  * `b`: the item difficulty (location)

**Alias:** `TwoPL`
