```
LocalOperator{T<:Number} <: AbstractMatrix{T}
```

Concrete type corresponding to a matrix operator acting on a tensor product of local vector  spaces. The operator acts as the matrix stored in the field `data` on the local vector spaces defined by the field `support`, and as the identity elsewhere. 

# Fields

  * `data::Matrix{T}`: stores the matrix represention of the operator
  * `support::UnitRange{Int}`: stores the sites that the operator has support on
