Representation of a symbol that may be bound to a key, depending on a keyboard layout. It differs from the physical representation of a key, denoted by names such as `AD01` which represent physical keys (in this case, `q` on a US keyboard). A key symbol is sent when a physical key is pressed, even if no input character is bound to the key. This structure provides a friendly `symbol` field, and a prettier `description` field (mostly used for printing). For example, the right arrow, with symbol `:right_arrow` (resp. `:kp_right_arrow` for keypad input), is represented by `"→"` (resp. `"→ (keypad)"`).

There is no consistent representation, so the one provided here may differ from windowing API implementations.

```julia
struct KeySymbol
```

  * `name::Symbol`
  * `description::Union{Char, String}`
