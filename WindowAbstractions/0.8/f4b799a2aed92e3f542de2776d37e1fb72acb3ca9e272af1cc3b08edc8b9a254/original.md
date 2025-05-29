Generic event structure identified by its type (see [`EventType`](@ref)) and which may hold data depending on the type of event.

The type of `data` follows the association (with respect to the event type):

  * `KEY_PRESSED` or `KEY_RELEASED`: [`KeyEvent`](@ref), accessible with `event.key_event`
  * `BUTTON_PRESSED` or `BUTTON_RELEASED`: [`MouseEvent`](@ref), accessible with `event.mouse_event`
  * `POINTER_MOVED`: [`PointerState`](@ref), accessible with `event.pointer_state`
  * `WINDOW_RESIZED`: `Tuple{Float64,Float64}` # new dimensions, accessible with `event.new_dimensions`
  * `WINDOW_EXPOSED`: `Tuple{Float64,Float64}` # area to redraw, accessible with `event.area`
  * Other event types: `Nothing`

```julia
struct Event{W<:WindowAbstractions.AbstractWindow}
```

  * `type::WindowAbstractions.EventType`
  * `data::Any`
  * `location::Tuple{Float64, Float64}`
  * `time::Float64`
  * `window::WindowAbstractions.AbstractWindow`
