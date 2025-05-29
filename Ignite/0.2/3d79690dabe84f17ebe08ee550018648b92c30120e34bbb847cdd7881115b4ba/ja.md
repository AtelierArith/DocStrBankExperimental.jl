```julia
struct EventHandler{E<:Ignite.AbstractEvent, H, A<:Tuple}
```

`EventHandler`は`event`と対応する`handler!`をラップします。`handler!`は、[`fire_event!`](@ref)への呼び出しによって`event`がトリガーされたときに実行されます。`handler!`からの出力は無視されます。`handler!`の追加の`args`は、構築時に`EventHandler`に保存される場合があります; [`add_event_handler!`](@ref)を参照してください。

`h::EventHandler`がトリガーされると、イベントハンドラーは`h.handler!(engine::Engine, h.args...)`として呼び出されます。

フィールド:

  * `event::Ignite.AbstractEvent`: ハンドラーをトリガーするイベント
  * `handler!::Any`: `event`によってトリガーされたときに実行されるイベントハンドラー
  * `args::Tuple`: イベントハンドラーに渡される追加の引数
