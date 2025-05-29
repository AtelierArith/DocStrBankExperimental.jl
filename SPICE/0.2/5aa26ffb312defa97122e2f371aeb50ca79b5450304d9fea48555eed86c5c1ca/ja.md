```
valid!(set::SpiceCell{T}) where T
```

任意のデータ型のSPICEセルから有効なSPICEセットを作成します。

### 引数

  * `set`: 検証されるセット

### 出力

順序付けられた要素と重複が削除された検証済みセットを返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/valid_c.html)
