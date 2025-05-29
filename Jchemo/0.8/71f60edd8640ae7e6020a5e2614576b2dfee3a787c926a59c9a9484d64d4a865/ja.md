```
rmrow(X::Union{AbstractMatrix, DataFrame}, s::Union{Vector, BitVector, UnitRange, Number})
rmrow(X::Union{Vector, BitVector}, s::Union{Vector, BitVector, UnitRange, Number})
```

行列の行またはベクトルのコンポーネントをインデックス `s` に基づいて削除します。

  * `X` : 行列またはベクトル。
  * `s` : インデックスのベクトル。

## 例

```julia
using Jchemo

X = rand(5, 2) 
rmrow(X, [1, 4])
```
