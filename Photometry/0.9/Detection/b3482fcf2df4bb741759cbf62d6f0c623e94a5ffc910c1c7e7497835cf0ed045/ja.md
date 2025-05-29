```
extract_sources(::SourceFinder, data, [error]; sorted=true)
```

`method`を使用して、点状のソースを見つけて抽出します。

`method`に関連する位置と情報を持つ`TypedTables.Table`を返します。たとえば、`PeakMesh`を使用すると、ピーク値の列を持つテーブルが返されます。

`data`は背景が引かれていると仮定されます。`error`が提供されると、それは検出アルゴリズムに伝播されます。`sorted`が`true`の場合、ソースはその振幅によってソートされます。

# 関連情報

  * [Source Detection Algorithms](@ref)
