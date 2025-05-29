Key binding associated to a character and a key modifier state.

```julia
struct KeyCombination
```

  * `key::WindowAbstractions.KeySymbol`
  * `exact_modifiers::WindowAbstractions.ModifierState`
  * `significant_modifiers::WindowAbstractions.ModifierState`
