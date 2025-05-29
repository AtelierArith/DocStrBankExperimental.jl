```
wrapdims(df, UniqueVector, :val, :x, :y)
```

Tables.jl テーブルを `KeyedArray` + `NamedDimsArray` ペアに変換します。値には列 `:val` を使用し、名前とキーには列 `:x, :y` を使用します。オプションの2番目の引数は、この型をすべてのキー・ベクトルに適用します。
