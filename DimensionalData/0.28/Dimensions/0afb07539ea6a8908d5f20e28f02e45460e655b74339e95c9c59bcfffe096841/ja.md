```
hasdim([f], x, query::Tuple) => NTuple{Bool}
hasdim([f], x, query...) => NTuple{Bool}
hasdim([f], x, query) => Bool
```

オブジェクト `x` が `query` の次元と一致するか、またはそれを継承しているかを確認します。

## 引数

  * `x`: `dims` メソッドを持つ任意のオブジェクト、`Dimension` のタプル、または単一の `Dimension`。
  * `query`: タプルまたは単一の `Dimension` または次元の `Type`。
  * `f`: デフォルトでは `<:` ですが、具体的な型に抽象型を一致させるために `>:` にすることもできます。

オブジェクトまたはタプルが `Dimension` を含むか、または次元のタプルを含むかを確認します。

## 例

```jldoctest
julia> using DimensionalData

julia> A = DimArray(ones(10, 10, 10), (X, Y, Z));

julia> hasdim(A, X)
true

julia> hasdim(A, (Z, X, Y))
(true, true, true)

julia> hasdim(A, Ti)
false
```
