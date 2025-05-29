```
getindex(var::ContextVar{T}) -> value::T
```

`var`に割り当てられた`value`を返します。未割り当ての場合は`KeyError`をスローします。
