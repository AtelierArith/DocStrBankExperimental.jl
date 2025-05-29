```
iter_agent_groups(order::Int, model::ABM; scheduler = Schedulers.by_id)
```

モデルのすべてのエージェントを順序でグループ化して返すイテレータを返します。`order = 2` の場合、イテレータはエージェントのペアを返します。例えば `(agent1, agent2)` のように、`order = 3` の場合はエージェントのトリプルを返します。例えば `(agent1, agent7, agent8)` のように。`order` は `1` より大きくなければなりませんが、上限はありません。

インデックスの順序は、スケジューラである `scheduler` 入力によって提供されます。
