```
abstract type ParamSparseMatrix{Tv,Ti,A<:AbstractSparseMatrix{Tv,Ti}
  } <: AbstractParamArray{Tv,2,A} end
```

Type representing parametric abstract sparse matrices of type A. Subtypes:

  * [`ParamSparseMatrixCSC`](@ref)
  * [`ParamSparseMatrixCSR`](@ref)
