```julia
grid_2d_agent(
;
    pos,
    space_type,
    agent_type,
    kwargs...
) -> EasyABM.Agent2D{Int64, EasyABM.PeriodicType, EasyABM.StaticType}

```

キーワード引数として指定されたプロパティを持つ単一の2Dエージェントを作成します。以下のプロパティ名は、特定のエージェントプロパティのために予約されています - pos : 位置 - vel : 速度 - shape : エージェントの形状 - color : エージェントの色 - size : エージェントのサイズ - orientation : エージェントの向き - `keeps_record_of` : エージェントが時間の進化中に記録するプロパティのセット。
