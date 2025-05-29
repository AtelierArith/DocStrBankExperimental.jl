```
save(agent)
```

エージェント階層を辞書に保存します。

デフォルトでは、各エージェントは次のフィールドを持つ辞書として表されます。

  * `type`: エージェントのタイプ、
  * `name`: エージェントの名前、
  * `arguments`（空でない場合）: 一般的なインターフェースプロパティ（`name`、`uuid`、`parent`、`opera` など）を除くエージェントのプロパティのベクトル、
  * `inners`（空でない場合）: 内部エージェントの表現を持つベクトル。

[`load`](@ref)も参照してください。

# 例

```julia
dump = save(agent)

# 出力
Dict(
    "type" => FreeAgent, "name" => "system", 
    "inners" => [
        Dict("name" => "alice", "type" => MyAgent{Float64}, "arguments" => Any[0.0, 1.0]),
        Dict("name" => "bob", "type" => MyAgent{Float64}, "arguments" => Any[0.0, 1.5]),
    ]
)
```
