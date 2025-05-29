```
aggregate!(method, dst::AbstractRaster, src::AbstractRaster, scale; skipmissing=false)
```

ラスタ `src` を `scale` によってラスタ `dst` に集約し、`method` を使用します。

# 引数

  * `method`: 複数のセルの値を組み合わせて集約セルを生成できる `mean` や `sum` のような関数、または `Start()` や `Center()` のような [`Locus`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.locus) で、区間内のサンプリング場所を指定します。
  * `scale`: 集約係数で、`Int`、各次元の `Int` の `Tuple`、または全次元を意味する `:` コロンを指定できます。通常 `getindex` で使用できる任意の `Dimension`、`Selector` または `Int` の組み合わせも使用できます。キーが次元名の `Pair` または `NamedTuple` の `Tuple` も機能します。`Selector` を使用すると、インデックスの開始からの距離によってスケールが決まります。セレクタは最初のオフセットを見つけ、残りの部分に対して同じ集約サイズを繰り返します。

集約 `scale` が配列の軸より大きい場合、軸の長さが使用されます。

# キーワード

  * `skipmissing`: `true` の場合、集約中に `missingval` はスキップされ、すべての欠損値の領域のみが `missingval(dst)` に集約されます。`false` の場合、1つ以上の `missingval` を含む集約領域には `missingval` が割り当てられます。デフォルトは `false` です。`skipmissing` の動作は関数 `f` とは独立しており、完全に非欠損値にのみ適用されます。
  * `progress`: 進行状況バーを表示します。デフォルトは `true` で、`false` にすると非表示になります。
  * `vebose`: 潜在的な問題に関するメッセージを印刷するかどうか。デフォルトは `true` です。

注意: 現在、メモリバックされたソース配列に対して集約する方が *はるかに* 速いです。必要に応じて使用前に `src` に対して [`read`](@ref) を使用してください。
