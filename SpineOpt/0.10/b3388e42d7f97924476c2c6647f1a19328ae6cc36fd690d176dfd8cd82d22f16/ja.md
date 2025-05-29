```
generate_stochastic_structure(m::Model)
```

与えられたSpineOptモデルのための確率構造を生成します。

確率構造は、有向非巡回グラフ（DAG）であり、頂点は`stochastic_scenario`オブジェクトであり、辺は`parent_stochastic_scenario__child_stochastic_scenario`関係によって与えられます。

その後、生成された構造をスライスするために`active_stochastic_paths`を呼び出すことができます。
