```
V = addfield(V::FEData,new_fields::NamedTuple; cellfield=false)
```

`new_fields` フィールドを `FEData` データセットに追加します。フィールドがセルフィールドの場合は `cellfield` を `true` に設定し、それ以外の場合は頂点フィールドになります。
