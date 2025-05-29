```
operator(mats::AbstractVector{<:AbstractMatrix}, inds::AbstractVector{<:AbstractVector}, B::AbstractBasis)
```

Constructor for `Operator`. 

## Inputs:

  * `mats`: List of matrices for local operators.
  * `inds`: List of sites on which local operators act.
  * `B`   : Basis.

## Outputs:

  * `O` : Operator.
