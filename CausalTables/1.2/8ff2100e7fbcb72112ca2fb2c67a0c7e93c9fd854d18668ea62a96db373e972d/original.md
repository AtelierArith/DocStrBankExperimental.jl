```
instruments(o::CausalTable, x::Symbol, y::Symbol)
```

Selects the instruments for a specific pair of variables (x,y) from the given `CausalTable` object; that is, variables that are associated with `x` but do not cause `y`.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the instruments.
  * `x::Symbol`, `y::Symbol`: The two variables whose instruments should be selected.

# Returns

A new `CausalTable` containing only the instruments of both x and y.
