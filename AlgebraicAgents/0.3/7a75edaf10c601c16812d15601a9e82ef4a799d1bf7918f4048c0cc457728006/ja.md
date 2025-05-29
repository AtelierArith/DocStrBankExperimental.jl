```
add_instantious!(opera, call, priority=0[, id])
add_instantious!(agent, call, priority=0[, id])
```

現在の時間ステップで実行される`call`をスケジュールします。

相互作用は、優先順位でソートされたインスタンス`Opera`内で実装されています。

[`Opera`](@ref)も参照してください。

# 例

```julia
add_instantious!(agent, () -> wake_up(agent))
```
