```
corner!(p::Path, α, sty::Style=discretestyle1(p))
```

Append a sharp turn or "corner" to path `p` with angle `α`.

The style chosen for this corner, if not specified, is the last `DiscreteStyle` used in the path.
