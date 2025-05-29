```
dnf(φ::Formula, literaltype = Literal; kwargs...)
```

Return a formula into Disjunctive Normal Form with literals of type `literaltype` (`CNF{literaltype}`). Any additional `kwarg` is internally passed to [`normalize`](@ref).
