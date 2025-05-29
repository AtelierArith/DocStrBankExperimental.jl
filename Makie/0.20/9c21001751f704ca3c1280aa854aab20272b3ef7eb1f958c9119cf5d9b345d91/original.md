```
to_align(align[, error_prefix])
```

Converts the given align to a `Vec2f`. Can convert `VecTypes{2}` and two component `Tuple`s with `Real` and `Symbol` elements.

To specify a custom error message you can add an `error_prefix` or use `halign2num(value, error_msg)` and `valign2num(value, error_msg)` respectively.
