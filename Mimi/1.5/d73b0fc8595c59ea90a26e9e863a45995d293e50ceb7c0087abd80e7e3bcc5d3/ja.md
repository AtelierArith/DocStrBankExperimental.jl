```
getdataframe(m::AbstractModel, comp_name::Symbol, pairs::Pair{Symbol, Symbol}...)
```

モデル `m` の指定された変数またはパラメータの値を持つ DataFrame を返します。`pairs` によって示される各ペアは `comp_name => item_name` の形式です。複数のペアが提供される場合、すべては同じ次元を持つアイテムを参照する必要があり、それぞれのアイテム値を結合するために使用されます。
