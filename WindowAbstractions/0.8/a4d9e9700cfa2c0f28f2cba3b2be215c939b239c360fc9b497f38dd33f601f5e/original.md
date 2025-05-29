```
save_history(wm::WM, queue::EventQueue{WM}) -> Vector{<:Event}
```

Save actions stored inside the event queue for later replay with [`replay_history`](@ref).

The event queue must have been created with `record_history = true`.
