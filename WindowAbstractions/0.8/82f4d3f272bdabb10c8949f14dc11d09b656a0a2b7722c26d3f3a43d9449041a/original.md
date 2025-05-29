Event queue meant to hold events to be processed by an application.

The event queue is bound to a window manager, and will be filled upon notification of low-level events sent by that window manager. Only high-level events will be recorded in the event queue, which are typically suited for use in applications.

The event queue is infinitely iterable, returning [`Event`](@ref)s as they are received. When no events are available, the queue will either enter a sleeping state of approximately 1 ms (if `sleep = true`) or spin while yielding at every iteration.

Any task iterating over the event queue is therefore a good candidate to be scheduled using an interactive thread from Julia 1.9 onwards.

Alternatively, the event queue may be manually filled with [`collect_events!`](@ref) and processed using `Base.isempty` and `Base.popfirst!`.

The parameter `record_history` may be set to `true` to save all events that have been processed (either by iteration or manual `Base.popfirst!`). Implementations of window managers may extend [`save_history`](@ref) and [`replay_history`](@ref) to allow for the saving and replay of events that have been stored. Note that `record_history` will have to be set to true for [`save_history`](@ref) to work.

```julia
struct EventQueue{WM<:WindowAbstractions.AbstractWindowManager, W<:WindowAbstractions.AbstractWindow}
```

  * `wm::WindowAbstractions.AbstractWindowManager`
  * `events::Array{WindowAbstractions.Event{W}, 1} where W<:WindowAbstractions.AbstractWindow`
  * `history::Array{WindowAbstractions.Event{W}, 1} where W<:WindowAbstractions.AbstractWindow`
  * `sleep::Bool`
  * `record_history::Bool`
