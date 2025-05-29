```julia
struct FilteredEvent{E<:Ignite.AbstractEvent, F} <: Ignite.AbstractEvent
```

`FilteredEvent(event::E, event_filter::F)` は `event` と `event_filter` 関数をラップします。

発火イベント `e` が発火するとき、もし `event_filter(engine, e)` が `true` を返すなら、フィルタされたイベントも発火します。

フィールド:

  * `event::Ignite.AbstractEvent`: フィルタ関数が発火イベントに適用されたときに `true` を返す場合に発火するラップされたイベント。
  * `event_filter::Any`: フィルタ関数 `(::Engine, ::AbstractFiringEvent) -> Bool` は、フィルタされたイベントが発火すべき場合に `true` を返します。
