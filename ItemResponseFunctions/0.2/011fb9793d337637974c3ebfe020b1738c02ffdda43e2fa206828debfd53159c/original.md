```julia
abstract type FiveParameterLogisticModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

An abstract representation of a 5 Parameter Logistic Model with an item response function given by

$P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = c_j + (d_j - c_j)\cdot\mathrm{logistic}(a_j(\theta_i - b_j))^{e_j}$

The item parameters `beta` must be a destructurable object with the following fields:

  * `a`: the item discrimination
  * `b`: the item difficulty (location)
  * `c`: the lower asymptote
  * `d`: the upper asymptote
  * `e`: the item stiffness

**Alias:** `FivePL`
