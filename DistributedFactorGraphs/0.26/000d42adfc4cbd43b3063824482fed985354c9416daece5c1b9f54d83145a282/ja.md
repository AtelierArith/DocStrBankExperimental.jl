```julia
deleteVariable!(dfg, variable)

```

DFGから参照されたVariableComputeを削除します。

ノート

  * `Tuple{AbstractDFGVariable, Vector{<:AbstractDFGFactor}}`を返します。
