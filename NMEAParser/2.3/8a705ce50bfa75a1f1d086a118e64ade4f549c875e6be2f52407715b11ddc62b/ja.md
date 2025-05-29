```
update(msg::T, s::NMEAData) where T <: NMEAString
```

NMEADataオブジェクトs内のタイプTの最後に受信したメッセージを、指定されたメッセージmsgで更新します。更新されたNMEADataオブジェクトsを返します。
