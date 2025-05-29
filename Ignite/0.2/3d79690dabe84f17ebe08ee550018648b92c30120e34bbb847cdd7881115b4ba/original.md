```julia
struct EventHandler{E<:Ignite.AbstractEvent, H, A<:Tuple}
```

`EventHandler`s wrap an `event` and a corresponding `handler!`. The `handler!` is executed when `event` is triggered by a call to [`fire_event!`](@ref). The output from `handler!` is ignored. Additional `args` for `handler!` may be stored in `EventHandler` at construction; see [`add_event_handler!`](@ref).

When `h::EventHandler` is triggered, the event handler is called as `h.handler!(engine::Engine, h.args...)`.

Fields: 

  * `event::Ignite.AbstractEvent`: Event which triggers handler
  * `handler!::Any`: Event handler which executes when triggered by `event`
  * `args::Tuple`: Additional arguments passed to the event handler
