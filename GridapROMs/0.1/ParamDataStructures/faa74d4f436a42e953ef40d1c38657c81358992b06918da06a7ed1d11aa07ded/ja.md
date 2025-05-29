```
abstract type ParamSparseMatrix{Tv,Ti,A<:AbstractSparseMatrix{Tv,Ti}
  } <: AbstractParamArray{Tv,2,A} end
```

型 A のパラメトリック抽象スパース行列を表す型。サブタイプ：

  * [`ParamSparseMatrixCSC`](@ref)
  * [`ParamSparseMatrixCSR`](@ref)
