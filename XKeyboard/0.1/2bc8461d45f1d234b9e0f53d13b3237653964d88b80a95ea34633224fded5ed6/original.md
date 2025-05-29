```
PhysicalKey(keymap::Keymap, name::Symbol)
```

Obtain a [`PhysicalKey`](@ref) from its string representation `name` using a keymap.

Useful for simulating events which typically require the integer code of a physical key (keycode).

A name of type `AbstractString` can be used instead if you have a string at the ready.
