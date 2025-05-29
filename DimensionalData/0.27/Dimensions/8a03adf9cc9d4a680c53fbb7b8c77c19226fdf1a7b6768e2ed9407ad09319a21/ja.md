```
setdims(X, newdims) => AbstractArray
setdims(::Tuple, newdims) => Tuple{Vararg{Dimension,N}}
```

最初の次元を `<: basetypeof(newdim)` に一致するものと置き換え、新しいオブジェクトまたはタプルを返して次元を更新します。

## 引数

  * `x`: `dims` メソッドを持つ任意のオブジェクト、`Dimension` のタプル、または単一の `Dimension`。
  * `newdim`: タプルまたは単一の `Dimension`、`Type` または `Symbol`。

# 例

```jldoctest
using DimensionalData, DimensionalData.Dimensions, DimensionalData.Lookups
A = ones(X(10), Y(10:10:100))
B = setdims(A, Y(Categorical('a':'j'; order=ForwardOrdered())))
lookup(B, Y)
# output
Categorical{Char} ForwardOrdered
wrapping: 'a':1:'j'
```
