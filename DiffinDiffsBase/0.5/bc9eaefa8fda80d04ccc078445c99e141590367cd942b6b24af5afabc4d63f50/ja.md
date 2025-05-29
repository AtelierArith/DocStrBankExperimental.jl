```
vcov(r::AbstractDIDResult, bys::Pair...)
```

指定された関数に基づいて選択された処置係数の分散共分散行列を返します。この関数は `true` または `false` のいずれかを返します。

関数 `f` が受け入れる引数に応じて、`bys` 引数は `column_index => f` または `column_indices => f` のいずれかとして指定されます。ここで、`column_index` は [`treatcells`](@ref) の列に対する `Symbol` または `Int` であり、`column_indices` は複数の列に対するそのようなインデックスの反復可能なコレクションです。`f` は指定された各列に要素ごとに適用され、係数を選択するための `BitVector` を取得します。複数の `Pair` が提供される場合、結果はビット単位の `and` を通じて1つの `BitVector` に結合されます。

!!! note
    このメソッドは処置係数の推定値のみを選択します。共変量は考慮されません。

