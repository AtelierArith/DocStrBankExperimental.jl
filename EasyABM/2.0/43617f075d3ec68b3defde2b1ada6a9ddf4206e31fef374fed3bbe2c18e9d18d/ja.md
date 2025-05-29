```julia
graph_agent(
;
    node,
    graph_mort_type,
    agent_type,
    kwargs...
) -> EasyABM.GraphAgent{EasyABM.StaticType, EasyABM.StaticType}

```

キーワード引数として指定されたプロパティを持つ単一のグラフエージェントを作成します。次のプロパティ名は、特定のエージェントプロパティのために予約されています - node : エージェントがグラフ上に位置するノード。 - shape : エージェントの形状 - color : エージェントの色 - size : エージェントのサイズ - orientation : エージェントの向き - `keeps_record_of` : エージェントが時間の進化中に記録するプロパティのセット。
