```
addstmtbefore!(fi::FuncInfo, id::Union{SSAValue, Int}, stmt)
```

Inserts a new statement before the statement identified by `id` in `FuncInfo`.  Returns the new `SSAValue` for the inserted statement. Equivalent to `addstmt!` + `insertbefore!`.
