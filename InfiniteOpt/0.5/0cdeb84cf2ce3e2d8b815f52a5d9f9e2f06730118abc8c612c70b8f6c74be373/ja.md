```
min_num_supports(data::AbstractMeasureData)::Int
```

`data`に関連付けられた最小サポート数を返します。フォールバックとして、これは単に`num_supports(data)`を返します。これは主に`FunctionalDiscreteMeasureData`の内部クエリを目的としていますが、必要に応じて他の測定データ型にも拡張できます。
