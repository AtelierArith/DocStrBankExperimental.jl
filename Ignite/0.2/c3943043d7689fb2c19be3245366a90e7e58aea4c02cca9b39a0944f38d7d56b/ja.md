```julia
struct OrEvent{E1<:Ignite.AbstractEvent, E2<:Ignite.AbstractEvent} <: Ignite.AbstractEvent
```

`OrEvent(event1, event2)` は2つのイベントをラップし、ラップされたイベントのいずれかが発火イベントによってトリガーされるとトリガーされます。

`OrEvent`は `|` 演算子を介して構築できます: `event1 | event2`。

フィールド:

  * `event1::Ignite.AbstractEvent`: 発火すべきかどうかがチェックされる最初のラップされたイベント。
  * `event2::Ignite.AbstractEvent`: 発火すべきかどうかがチェックされる2番目のラップされたイベント。
