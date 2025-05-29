```
insertbefore!(fi::FuncInfo, id::Union{SSAValue, Int}, stmtid::Union{SSAValue, Int})
```

Inserts the statement identified by `stmtid` before the statement identified by `id` in `FuncInfo`.
