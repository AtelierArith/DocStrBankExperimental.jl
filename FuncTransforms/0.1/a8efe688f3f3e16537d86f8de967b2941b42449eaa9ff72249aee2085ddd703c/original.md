```
insertafter!(fi::FuncInfo, id::Union{SSAValue, Int}, stmtid::Union{SSAValue, Int})
```

Inserts the statement identified by `stmtid` after the statement identified by `id` in `FuncInfo`.
