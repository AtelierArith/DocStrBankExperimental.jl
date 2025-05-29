```
load(hierarchy; eval_scope=Main)
```

辞書からエージェント階層をインスタンス化します。

デフォルトでは、各エージェントは次のフィールドを持つ辞書として表されます。

  * `type`: エージェントのタイプ。この値はタイプ名を含む文字列または実際のタイプであることができます。
  * `name`: エージェントの名前。
  * `arguments`（空でない場合）: 一般的なインターフェースプロパティ（`name`、`uuid`、`parent`、`opera`など）を除くエージェントのプロパティのベクター。
  * `inners`（空でない場合）: 内部エージェントの表現を持つベクター。

例えば、

```julia
Dict(
    "type" => FreeAgent, "name" => "system", 
    "inners" => [
        Dict("name" => "alice", "type" => MyAgent{Float64}, "arguments" => Any[0.0, 1.0]),
        Dict("name" => "bob", "type" => MyAgent{Float64}, "arguments" => Any[0.0, 1.5]),
    ]
)
```

内部的に、このメソッドは提供された `hierarchy` 辞書からカプセル化されたエージェントのタイプを取得し、その上で `_load(type, hierarchy; eval_scope)` を呼び出します。このプロセスは、カプセル化されたエージェントと、`hierarchy` 内に含まれるすべての関連する内部エージェントをインスタンス化します。

[`load`](@ref) も参照してください。
