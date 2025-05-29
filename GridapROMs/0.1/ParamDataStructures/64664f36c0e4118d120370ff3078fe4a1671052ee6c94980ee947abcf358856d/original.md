```
abstract type ParamArray{T,N} <: AbstractParamArray{T,N,Array{T,N}} end
```

Type representing parametric arrays of type A. Subtypes:

  * [`TrivialParamArray`](@ref)
  * [`ConsecutiveParamArray`](@ref)
  * [`GenericParamVector`](@ref)
  * [`GenericParamMatrix`](@ref)
  * [`ArrayOfArrays`](@ref)
  * [`BlockParamArray`](@ref)

Also acts as a constructor according to the following rules:

  * ParamArray(A::AbstractArray{<:Number}) -> ParamNumber
  * ParamArray(A::AbstractArray{<:Number},plength::Int) -> TrivialParamArray
  * ParamArray(A::AbstractVector{<:AbstractArray}) -> ParamArray
  * ParamArray(A::AbstractVector{<:AbstractSparseMatrix}) -> ParamSparseMatrix
  * ParamArray(A::AbstractArray{<:ParamArray}) -> BlockParamArray
