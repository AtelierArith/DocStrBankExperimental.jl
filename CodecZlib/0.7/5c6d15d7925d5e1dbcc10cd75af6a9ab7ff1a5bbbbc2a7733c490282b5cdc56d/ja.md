```
DeflateDecompressor(;windowbits=15)
```

デフレートデコンプレスコーデックを作成します。

## 引数

  * `windowbits` (8..15): `windowbits`をデフォルトの15から変更すると、`2^windowbits`より大きい履歴バッファを使用してデータをデコードすることができなくなります。

!!! warning
    `serialize`および`deepcopy`は、保存された生ポインタのため、このコーデックでは機能しません。

