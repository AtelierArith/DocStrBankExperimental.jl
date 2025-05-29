```julia
abstract type OneParameterLogisticModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

An abstract representation of a 1 Parameter Logistic Model with an item response function given by

$P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = \mathrm{logistic}(\theta_i - b_j)$

The item parameter `beta` can be passed as a number or a destructurable object with the following fields:

  * `b`: the item difficulty (location)

**Alias:** `OnePL`
