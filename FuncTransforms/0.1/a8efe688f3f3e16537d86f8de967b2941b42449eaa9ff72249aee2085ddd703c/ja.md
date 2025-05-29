```
insertafter!(fi::FuncInfo, id::Union{SSAValue, Int}, stmtid::Union{SSAValue, Int})
```

`FuncInfo`内の`id`によって識別されるステートメントの後に、`stmtid`によって識別されるステートメントを挿入します。
