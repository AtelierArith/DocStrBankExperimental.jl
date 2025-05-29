```
ModifiedKey
```

A key with modifiers. Conveniently constructed with `|`, e.g. `ctrl | CharKey('a')` for Ctrl+A.  Note that not all combinations are useable. For example, Ctrl+J and Ctrl+M are both identical to [RETURN].

Combining with `|` is nearly always more readable, e.g. `alt | ctrl | CharKey('q')` instead of `ModKey(0x03, CharKey('q')`

# Fields

mod_bitmap::UInt8 - Modifier key bitmap; From LSB: Alt, Ctrl, Shift key::Union{CharKey, SpecialKey} - The base key
