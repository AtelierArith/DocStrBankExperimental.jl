```
@call agent call [priority[, id]]
@call opera call [priority[, id]]
```

現在の時間ステップで実行されるインタラクション（コール）をスケジュールします。ここで、`call`は関数`() -> call`に変換されます。

インタラクションは、優先順位でソートされたインスタンス`Opera`内に実装されています。

詳細は[`Opera`](@ref)を参照してください。

# 例

```julia
bob_agent = only(getagent(agent, r"bob"))
@call agent wake_up(bob_agent) # translates into `() -> wake_up(bob_agent)`
```
