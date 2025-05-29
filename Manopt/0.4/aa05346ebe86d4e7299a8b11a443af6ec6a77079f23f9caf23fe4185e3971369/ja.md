```
get_index(rs::RecordSolverState, s::Symbol)
ro[s]
```

記録されたタイプ `s` の記録された値を取得します。詳細については [`get_record`](@ref) を参照してください。

```
get_index(rs::RecordSolverState, s::Symbol, i...)
ro[s, i...]
```

タイプ `s` の記録タイプにアクセスし、その [`RecordAction`](@ref) を `[i...]` で呼び出します。
