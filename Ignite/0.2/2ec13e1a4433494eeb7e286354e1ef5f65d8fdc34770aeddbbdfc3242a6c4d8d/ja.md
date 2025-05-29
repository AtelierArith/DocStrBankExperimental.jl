```julia
add_event_handler!(
    handler!,
    engine::Ignite.Engine,
    event::Ignite.AbstractEvent,
    handler_args...
) -> Ignite.Engine

```

`event` がトリガーされたときに発火するエンジンにイベントハンドラーを追加します。

発火すると、イベントハンドラーは `handler!(engine::Engine, handler_args...)` として呼び出されます。
