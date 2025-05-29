```
rmcol(X::Union{AbstractMatrix, DataFrame}, s::Union{Vector, BitVector, UnitRange, Number})
rmcol(X::Vector, s::Union{Vector, BitVector, UnitRange, Number})
```

行列の列またはベクトルのコンポーネントをインデックス `s` を持つものを削除します。

  * `X` : 行列またはベクトル。
  * `s` : インデックスのベクトル。

## 例

```julia
using Jchemo

X = rand(5, 3) 
rmcol(X, [1, 3])
```
