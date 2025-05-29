```julia
deleteVariable!(dfg, variable)

```

DFGから参照されたDFGVariableを削除します。

ノート

  * `Tuple{AbstractDFGVariable, Vector{<:AbstractDFGFactor}}`を返します。
