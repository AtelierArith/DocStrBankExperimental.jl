```
symparsestring(s::String)::Vector{Any}
```

Parse `s` into an array of Symata expressions, with one expression per array element.

The Symata expressions are not evaluated. For example `symparsestring("b + b")` returns the Symata expression `Plus(b, b)`, rather than  `Times(2, b)`.

Note that the phrase *Symata expression* includes numbers, symbols, etc.

See `symparseeval`.
