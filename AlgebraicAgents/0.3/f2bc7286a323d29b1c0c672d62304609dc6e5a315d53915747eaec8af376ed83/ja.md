```
add_control!(opera, call[, id])
add_control!(agent, call[, id])
```

システムに制御を追加します。オプションで、アクションのテキスト識別子 `id` を提供します。

ここで、`call` は次のいずれかの形式に従う必要があります：     - パラメータなし、     - `Opera` インスタンスの関数、     - 階層内の最上位エージェントの関数。これは動的ディスパッチに従います。

詳細は [`@control`](@ref) と [`Opera`](@ref) を参照してください。

# 例

```julia
system = MyAgentType("system")
control = agent -> agent.temp > 100 && cool!(agent)
add_control!(system, () -> control(system), "temperature control")
```
