```
otherdims(x, query) => Tuple{Vararg{Dimension,N}}
```

`query`に含まれないオブジェクトの次元を取得します。

## 引数

  * `x`: `dims`メソッドを持つ任意のオブジェクト、`Dimension`の`Tuple`。
  * `query`: `Tuple`または単一の`Dimension`または次元の`Type`。
  * `f`: デフォルトでは`<:`ですが、具体的な型に抽象型を一致させるために`>:`にすることもできます。

一致しない次元を保持するタプルが常に返されます。

## 例

```jldoctest
julia> using DimensionalData, DimensionalData.Dimensions

julia> A = DimArray(ones(10, 10, 10), (X, Y, Z));

julia> otherdims(A, X)
Y, Z

julia> otherdims(A, (Y, Z))
X
```
