```
抽象型 ParamArray{T,N} <: AbstractParamArray{T,N,Array{T,N}} end
```

型 A のパラメトリック配列を表します。サブタイプ:

  * [`TrivialParamArray`](@ref)
  * [`ConsecutiveParamArray`](@ref)
  * [`GenericParamVector`](@ref)
  * [`GenericParamMatrix`](@ref)
  * [`ArrayOfArrays`](@ref)
  * [`BlockParamArray`](@ref)

以下のルールに従ってコンストラクタとしても機能します:

  * ParamArray(A::AbstractArray{<:Number}) -> ParamNumber
  * ParamArray(A::AbstractArray{<:Number},plength::Int) -> TrivialParamArray
  * ParamArray(A::AbstractVector{<:AbstractArray}) -> ParamArray
  * ParamArray(A::AbstractVector{<:AbstractSparseMatrix}) -> ParamSparseMatrix
  * ParamArray(A::AbstractArray{<:ParamArray}) -> BlockParamArray
