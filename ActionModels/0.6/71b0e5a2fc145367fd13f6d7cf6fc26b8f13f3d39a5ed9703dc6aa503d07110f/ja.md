```
get_states(agent::Agent, target_state::Union{String,Tuple})
```

エージェントから単一の状態を取得します。単一の値を返します。

```
get_states(agent::Agent, target_state::Vector)
```

エージェントから状態値のセットを取得します。状態名とその値の辞書を返します。

```
get_states(agent::Agent)
```

エージェントからすべての状態を取得します。状態名とその値の辞書を返します。
