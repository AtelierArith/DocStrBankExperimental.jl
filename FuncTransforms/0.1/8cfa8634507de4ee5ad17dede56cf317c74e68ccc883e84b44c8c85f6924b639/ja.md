```
insertbefore!(fi::FuncInfo, id::Union{SSAValue, Int}, stmtid::Union{SSAValue, Int})
```

`stmtid`で識別されるステートメントを、`id`で識別されるステートメントの前に`FuncInfo`に挿入します。
