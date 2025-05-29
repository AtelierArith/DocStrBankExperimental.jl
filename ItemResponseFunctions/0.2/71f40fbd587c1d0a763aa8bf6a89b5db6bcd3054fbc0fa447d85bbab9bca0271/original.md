```julia
abstract type PartialCreditModel <: ItemResponseFunctions.PolytomousItemResponseModel
```

An abstract type representing a Partial Credit Model with an item category response function given by

$P(Y_{ij} = y,| \theta_i, \boldsymbol{\beta}_j) =     \frac{\exp \sum_{s=1}^y (\theta_i - b_j + t_{js})}     {1 + \sum_{k=1}^{K_j} \exp \sum_{s=1}^k (\theta_i - b_j + t_{js})}$

The item parameters `beta` must be a destructurable object with the following fields:

  * `b`: the item difficulty (location)
  * `t`: a vector of threshold parameters

**Alias:** `PCM`
