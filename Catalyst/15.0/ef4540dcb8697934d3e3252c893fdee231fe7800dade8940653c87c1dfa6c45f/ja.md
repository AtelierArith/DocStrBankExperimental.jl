```
SymbolicUtils.setmetadata(rx::Reaction, key::Symbol, val)
```

キー `key` でメタデータを値 `val` に設定します。すでに存在する場合は上書きし、存在しない場合は追加します。

引数:

  * `rx`: メタデータを追加する反応。
  * `key`: メタデータのキーを表す `Symbol` (すなわち名前)。
  * `val`: メタデータの値。
