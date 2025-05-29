```
replacestmt!(fi::FuncInfo, id::Union{SSAValue, Int}, stmt)
```

Replaces the statement at the given SSA Value `id` in `FuncInfo`'s code block with a new statement.
