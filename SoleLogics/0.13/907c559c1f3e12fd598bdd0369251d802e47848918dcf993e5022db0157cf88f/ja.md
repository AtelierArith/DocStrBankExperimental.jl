```
cnf(φ::Formula, literaltype = Literal; kwargs...)
```

リテラルの型 `literaltype` (`CNF{literaltype}`) を持つ論理式を論理積標準形に変換します。追加の `kwarg` は内部的に [`normalize`](@ref) に渡されます。
