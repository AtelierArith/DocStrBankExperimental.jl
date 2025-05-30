```
default_library(d::FullDim, ::Type{T}) where {T}
```

`T`型の`d`次元多面体のデフォルトポリヘドラライブラリを返します。

## 例

`Float64`のeltypeを持つ2次元多面体のデフォルトライブラリを取得するには、`default_library(2, Float64)`を実行します。

`StaticArrays.SVector`型の`v`がある場合、`v`の型に対して型安定な方法でポイントのデフォルトライブラリを取得するには、`default_library(Polyhedra.FullDim(v), eltype(v))`を実行します。
