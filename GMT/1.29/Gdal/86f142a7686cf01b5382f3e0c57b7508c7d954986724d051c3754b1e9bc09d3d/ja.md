```
setproj!(type, proj)
```

`type`オブジェクトに参照システムを設定します。このオブジェクトは`GMTgrid`、`GMTimage`、`GMTdataset`、または`AbstractDataset`であることができます。

  * `proj`は、Proj4文字列またはWKTのいずれかです。あるいは、別のグリッド、画像、またはデータセットタイプである場合、その参照システムが`type`にコピーされます。
