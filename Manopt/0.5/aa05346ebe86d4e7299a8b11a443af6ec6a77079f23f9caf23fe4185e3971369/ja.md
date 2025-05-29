```
get_index(rs::RecordSolverState, s::Symbol)
ro[s]
```

記録された型 `s` の記録された値を取得します。詳細については [`get_record`](@ref) を参照してください。

```
get_index(rs::RecordSolverState, s::Symbol, i...)
ro[s, i...]
```

型 `s` の記録型にアクセスし、その [`RecordAction`](@ref) を `[i...]` で呼び出します。
