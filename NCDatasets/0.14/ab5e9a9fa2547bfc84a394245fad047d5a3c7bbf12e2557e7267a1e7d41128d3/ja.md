```
names = dimnames(ds::AbstractNCDataset; parents = false)
```

`ds`で定義されたすべての名前を返します。`parents`が`true`の場合、親グループの名前も返されます（デフォルトは`false`です）。
