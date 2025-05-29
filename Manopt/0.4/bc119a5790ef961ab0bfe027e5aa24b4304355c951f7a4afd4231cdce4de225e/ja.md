```
update_stopping_criterion!(c::Stoppingcriterion, s::Symbol, v::value)
update_stopping_criterion!(s::AbstractManoptSolverState, symbol::Symbol, v::value)
update_stopping_criterion!(c::Stoppingcriterion, ::Val{Symbol}, v::value)
```

停止基準内の値を、シンボル `s` で指定された `v` に更新します。もし基準に `s` に対応する値が割り当てられていない場合、更新は無視されます。

2 番目のシグネチャでは、[`AbstractManoptSolverState`](@ref) `o` 内の停止基準が更新されます。

どのシンボルがどの値を更新するかを確認するには、特定の停止基準を参照してください。これらはシンボル値ごとにディスパッチを使用する必要があります（3 番目のシグネチャ）。
