```julia
abstract type OneParameterLogisticPlusGuessingModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

An abstract representation of the 1 Parameter Logistic + Guessing Model with an item response function given by

$P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = c + (1 - c) \cdot \mathrm{logistic}(\theta_i - b_j)$

The item parameters `beta` must be a destructurable object with the following fields:

  * `b`: the item difficulty (location)
  * `c`: the lower asymptote

**Alias:** `OnePLG`
