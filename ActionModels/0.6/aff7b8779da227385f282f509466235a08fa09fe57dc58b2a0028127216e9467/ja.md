```
get_history(agent::Agent, target_state::Union{String,Tuple})
```

エージェントから単一の状態の履歴を取得します。ベクターを返します。

```
get_history(agent::Agent, target_states::Vector)
```

エージェントから状態のベクターのセットを取得します。状態とその履歴の辞書を返します。

```
get_history(agent::Agent)
```

エージェントから状態の履歴を取得します。状態とその履歴の辞書を返します。
