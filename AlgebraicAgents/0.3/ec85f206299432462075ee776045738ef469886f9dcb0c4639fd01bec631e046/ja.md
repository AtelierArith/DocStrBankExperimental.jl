```
@future opera time call [id]
@future agent time call [id]
```

`call`を`time`で（遅延）実行するスケジュールを設定します。オプションで、アクションのテキスト識別子`id`を提供します。

`call`は式であり、`@future`が呼び出されたときにクロージャを取る関数`() -> call`にラップされます。

[`@future`](@ref)および[`Opera`](@ref)も参照してください。

# 例

```julia
alice = MyAgentType("alice")
interact = agent -> wake_up!(agent)
@future alice 5.0 interact(alice) "alice_schedule" # `t=5`で停止
```
