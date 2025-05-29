```
eval_supports(vref::SemiInfiniteVariableRef)::Dict{Int, Float64}
```

半無限変数 `vref` に関連付けられた評価サポートを返します。

**例**

```julia-repl
julia> eval_supports(vref)
Dict{Int64,Float64} with 1 entry:
  1 => 0.5
```
