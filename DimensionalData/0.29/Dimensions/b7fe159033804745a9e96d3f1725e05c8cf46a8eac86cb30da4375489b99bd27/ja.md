```
dims(x, query) => Tuple{Vararg{Dimension}}
dims(x, query...) => Tuple{Vararg{Dimension}}
```

クエリ次元の型に一致する次元を取得します。

ルックアップは Int または Dimension であるか、いずれかの組み合わせを含むタプルであることができます。

## 引数

  * `x`: `dims` メソッドを持つ任意のオブジェクト、または `Dimension` の `Tuple`。
  * `query`: タプルまたは単一の `Dimension` または `Dimension` の `Type`。

## 例

```jldoctest
julia> using DimensionalData

julia> A = DimArray(ones(2, 3, 2), (X, Y, Z))
┌ 2×3×2 DimArray{Float64, 3} ┐
├────────────────────── dims ┤
  ↓ X, → Y, ↗ Z
└────────────────────────────┘
[:, :, 1]
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> dims(A, (X, Y))
(↓ X, → Y)

```
