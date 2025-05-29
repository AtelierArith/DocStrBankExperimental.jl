```
get_taped_globals(T::Type)
```

When called from inside a call to a `TapedTask`, this will return whatever is contained in its `taped_globals` field.

The type `T` is required for optimal performance. If you know that the result of this operation must return a specific type, specify `T`. If you do not know what type it will return, pass `Any` – this will typically yield type instabilities, but will run correctly.

See also [`set_taped_globals!`](@ref).
