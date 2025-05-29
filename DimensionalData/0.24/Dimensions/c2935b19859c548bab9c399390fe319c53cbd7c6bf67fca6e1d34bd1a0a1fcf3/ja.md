```
dimnum(x, query::Tuple) => NTuple{Int}
dimnum(x, query) => Int
```

オブジェクトの次元における順序で `Dimension` の数を取得します。

## 引数

  * `x`: `dims` メソッドを持つ任意のオブジェクト、`Dimension` の `Tuple` または単一の `Dimension`。
  * `query`: `Tuple`、配列、または単一の `Dimension` または次元の `Type`。

戻り値の型は、`query` が `Tuple` か単一の `Dimension` に応じて、`Int` の `Tuple` または単一の `Int` になります。

## 例

```jldoctest
julia> using DimensionalData

julia> A = DimArray(ones(10, 10, 10), (X, Y, Z));

julia> dimnum(A, (Z, X, Y))
(3, 1, 2)

julia> dimnum(A, Y)
2
```
