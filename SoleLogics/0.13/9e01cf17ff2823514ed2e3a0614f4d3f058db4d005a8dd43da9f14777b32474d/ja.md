```
dnf(φ::Formula, literaltype = Literal; kwargs...)
```

リテラルタイプ `literaltype` (`CNF{literaltype}`) の論理式を論理和標準形に変換します。追加の `kwarg` は内部的に [`normalize`](@ref) に渡されます。
