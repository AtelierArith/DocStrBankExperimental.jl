```
V = addfield(V::Q1Data,new_fields::NamedTuple; cellfield=false)
```

`Q1Data` データセットに `new_fields` フィールドを追加します。フィールドがセルフィールドの場合は `cellfield` を `true` に設定し、それ以外の場合は頂点フィールドになります。
