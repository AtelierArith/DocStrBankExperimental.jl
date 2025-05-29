```
requires_exactly1(method::AbstractReformulationMethod)
```

Return a `Bool` whether `method` requires that `Exactly 1` disjunct be selected  as true for each disjunction. For new reformulation method types, this should be  extended to return `true` if such a constraint is required (defaults to `false` otherwise).
