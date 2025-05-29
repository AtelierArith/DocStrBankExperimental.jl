```julia
abstract type AbstractSolutionArray{T, N} <: AbstractArray{T, N}
```

定常解のための抽象型。`AbstractArray`のサブタイプ。
