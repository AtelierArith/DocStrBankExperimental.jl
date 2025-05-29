```
extract_plot_coords([T::Type{<:AbstractFloat} = Float32], item)
```

指定された `item` に含まれるすべての点の対応する座標を含む2つのベクトル `lat` と `lon` を持つ NamedTuple を返します。

これは主に、`PlotlyBase` の `scattergeo` 関数に提供するための `lat` と `lon` キーワード引数の作成を簡素化することを目的としています。デフォルトでは、点は Float32 に変換され、複数のポリエリアを単一のトレース内でプロットできるように、各 `Ring` の間に NaN 値が挿入されます。
