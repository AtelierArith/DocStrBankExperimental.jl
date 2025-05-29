```
addstmtafter!(fi::FuncInfo, id::Union{SSAValue, Int}, stmt)
```

`FuncInfo`内の`id`で識別される文の後に新しい文を挿入します。挿入された文の新しい`SSAValue`を返します。`addstmt!` + `insertafter!`と同等です。
