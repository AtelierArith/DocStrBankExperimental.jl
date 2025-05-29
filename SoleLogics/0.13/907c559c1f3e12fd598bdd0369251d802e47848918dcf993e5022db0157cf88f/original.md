```
cnf(φ::Formula, literaltype = Literal; kwargs...)
```

Return a formula into Conjunctive Normal Form with literals of type `literaltype` (`CNF{literaltype}`). Any additional `kwarg` is internally passed to [`normalize`](@ref).
