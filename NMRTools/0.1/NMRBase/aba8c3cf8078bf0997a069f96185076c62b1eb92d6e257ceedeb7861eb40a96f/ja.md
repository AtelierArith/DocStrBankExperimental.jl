```
add_offset!(data::NMRData, dim_ref, offset)
```

NMRDataオブジェクトの周波数次元にオフセットを追加します。次元は数値インデックスまたは`F1Dim`のようなオブジェクトとして指定できます。メタデータは`replacedimension`を使用してコピーされ、オフセットの変更を記録するために次元メタデータにエントリが追加または更新されます。
