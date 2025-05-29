```
replacestmt!(fi::FuncInfo, id::Union{SSAValue, Int}, stmt)
```

指定されたSSA値`id`の文を`FuncInfo`のコードブロック内で新しい文に置き換えます。
