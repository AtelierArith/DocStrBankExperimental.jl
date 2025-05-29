```
get_slot(ci::CodeInfo, s::Symbol)
```

`ci::CodeInfo`内の`s::Symbol`に関連付けられた`Core.Compiler.SlotNumber`を取得します。関連付けられた`Core.Compiler.SlotNumber`がない場合は、`nothing`を返します。
