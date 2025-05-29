```
write_event!(cast::Cast, event_type::EventType, event_data::AbstractString)
write_event!(cast::Cast, event::Event)
```

`cast` に `event_type` のタイプ（`OutputEvent` または `InputEvent` のいずれか）で、`event_data` によって与えられたデータを持つイベントを書き込みます。
