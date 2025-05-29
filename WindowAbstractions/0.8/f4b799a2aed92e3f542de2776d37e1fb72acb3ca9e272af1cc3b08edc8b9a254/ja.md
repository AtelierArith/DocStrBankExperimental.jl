イベントの種類によって識別される汎用イベント構造体（[`EventType`](@ref）を参照）であり、イベントの種類に応じてデータを保持することがあります。

`data`の型は、イベントタイプに関する関連に従います：

  * `KEY_PRESSED`または`KEY_RELEASED`：[`KeyEvent`](@ref)、`event.key_event`でアクセス可能
  * `BUTTON_PRESSED`または`BUTTON_RELEASED`：[`MouseEvent`](@ref)、`event.mouse_event`でアクセス可能
  * `POINTER_MOVED`：[`PointerState`](@ref)、`event.pointer_state`でアクセス可能
  * `WINDOW_RESIZED`：`Tuple{Float64,Float64}` # 新しい寸法、`event.new_dimensions`でアクセス可能
  * `WINDOW_EXPOSED`：`Tuple{Float64,Float64}` # 再描画する領域、`event.area`でアクセス可能
  * その他のイベントタイプ：`Nothing`

```julia
struct Event{W<:WindowAbstractions.AbstractWindow}
```

  * `type::WindowAbstractions.EventType`
  * `data::Any`
  * `location::Tuple{Float64, Float64}`
  * `time::Float64`
  * `window::WindowAbstractions.AbstractWindow`
