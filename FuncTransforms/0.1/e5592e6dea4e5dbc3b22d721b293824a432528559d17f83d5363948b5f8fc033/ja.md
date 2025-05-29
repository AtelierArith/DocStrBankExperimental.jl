```
addstmtbefore!(fi::FuncInfo, id::Union{SSAValue, Int}, stmt)
```

`FuncInfo`内の`id`で識別される文の前に新しい文を挿入します。挿入された文の新しい`SSAValue`を返します。`addstmt!` + `insertbefore!`と同等です。
