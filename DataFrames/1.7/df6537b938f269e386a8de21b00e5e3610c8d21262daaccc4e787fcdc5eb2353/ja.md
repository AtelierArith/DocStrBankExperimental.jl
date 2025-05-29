```
similar(df::AbstractDataFrame, rows::Integer=nrow(df))
```

`df`と同じ列名と列要素型を持つ新しい`DataFrame`を作成します。オプションの第二引数を提供することで、`df`に存在する行数とは異なる行数を要求することができます。

メタデータ: この関数は、テーブルレベルおよび列レベルの`:note`スタイルのメタデータを保持します。
