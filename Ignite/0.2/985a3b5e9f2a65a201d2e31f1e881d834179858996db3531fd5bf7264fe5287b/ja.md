```julia
struct AndEvent{E1<:Ignite.AbstractEvent, E2<:Ignite.AbstractEvent} <: Ignite.AbstractEvent
```

`AndEvent(event1, event2)` は2つのイベントをラップし、両方のラップされたイベントが同じ発火イベントによってトリガーされた場合にのみトリガーされます。

`AndEvent`は `&` 演算子を介して構築できます: `event1 & event2`。

フィールド:

  * `event1::Ignite.AbstractEvent`: トリガーの対象となる最初のラップされたイベント。
  * `event2::Ignite.AbstractEvent`: トリガーの対象となる2番目のラップされたイベント。
