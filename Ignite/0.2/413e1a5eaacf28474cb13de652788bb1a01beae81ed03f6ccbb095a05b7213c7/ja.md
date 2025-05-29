```julia
fire_event!(
    engine::Ignite.Engine,
    e::Ignite.AbstractFiringEvent
) -> Ignite.Engine

```

発火イベント `e` によってトリガーされたすべてのイベントハンドラーを実行します。
