```
StabilityReport()
StabilityReport(unstable_variables::Vector{Tuple{Symbol, Type}})
```

メソッドの安定性に関する情報を保持します。

`unstable_vars` が存在する場合、フィールドを設定します。そうでない場合は、空のセットを作成します。

[`is_stable`](@ref) を参照してください。
