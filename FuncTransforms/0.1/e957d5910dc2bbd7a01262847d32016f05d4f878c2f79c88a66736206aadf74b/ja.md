```
addstmt!(fi::FuncInfo, stmt)
```

`FuncInfo`に新しいステートメントを追加しますが、コードブロックには挿入しません。新しい`SSAValue`を返します。
