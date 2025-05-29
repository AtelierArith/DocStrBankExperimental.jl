```
stmt_effect_flags(stmt, rt, src::Union{IRCode,IncrementalCompact}) ->
    (consistent::Bool, removable::Bool, nothrow::Bool)
```

与えられたステートメントのための `(:consistent, :removable, :nothrow)` フラグのタプルを返します。
