```
add_callback!(simulation, callback::Callback; name = GenericName(), callback_kw...)

add_callback!(simulation, func, schedule=IterationInterval(1); name = GenericName(), callback_kw...)
```

Add `Callback(func, schedule)` to `simulation.callbacks` under `name`. The default `GenericName()` generates a name of the form `:callbackN`, where `N` is big enough for the name to be unique.

If `name::Symbol` is supplied, it may be modified if `simulation.callbacks[name]` already exists.

`callback_kw` are passed to the constructor for [`Callback`](@ref).

The `callback` (which contains a schedule) can also be supplied directly.
