```
getdataframe(m::AbstractModel, pair::Pair{Symbol, NTuple{N, Symbol}})
```

指定された変数またはパラメータに対する値を持つDataFrameを返します。`pairs`によって示される各ペアは、`comp_name => item_name`の形式です。複数のペアが提供される場合、すべてが同じ次元のアイテムを参照する必要があり、それらはそれぞれのアイテム値を結合するために使用されます。
