```
add_future!(opera, time, call[, id])
add_future!(agent, time, call[, id])
```

`call`を`time`で（遅延）実行するようにスケジュールします。オプションで、アクションのテキスト識別子`id`を提供します。

ここで、`call`は次のいずれかの形式に従う必要があります：     - パラメータなし、     - `Opera`インスタンスの関数、     - 階層内の最上位エージェントの関数。これは動的ディスパッチに従います。

[`Opera`](@ref)も参照してください。

# 例

```julia
alice = MyAgentType("alice")
interact = agent -> wake_up!(agent)
add_future!(alice, 5.0, () -> interact(alice), "alice_schedule")
```
