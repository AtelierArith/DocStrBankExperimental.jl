Details surrounding an event produced by a keystroke.

```julia
struct KeyEvent
```

  * `key_name::Symbol`: The name of the physical key.

  * `key::WindowAbstractions.KeySymbol`: The symbol associated with the keystroke.

  * `input::Char`: Printable input (can be the empty string).

  * `modifiers::WindowAbstractions.ModifierState`: Modifier state.

  * `consumed_modifiers::WindowAbstractions.ModifierState`: Modifiers that were used when translating the physical key into a key symbol.
