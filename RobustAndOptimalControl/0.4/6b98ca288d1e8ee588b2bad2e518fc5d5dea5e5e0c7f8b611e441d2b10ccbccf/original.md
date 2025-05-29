```
expand_symbol(s::Symbol, n::Int)
```

Takes a symbol and an integer and returns a vector of symbols with increasing numbers appended to the end. E.g., (:x, 3) -> [:x1, :x2, :x3]

The short-hand syntax `s^n` is also available, e.g., `:x^3 == expand_symbol(:x, 3)`.

Useful to create signal names for named systems.
