```
ProductGroupOperation{O<:NTuple{N,AbstractGroupOperation} where N} <: AbstractProductGroupOperation
```

グループ演算のタプルをモデル化する構造体で、積群の各因子ごとに1つの演算があり、それらが一緒になって新しい群演算を形成します。

単一の演算へのアクセスは `pgo[i]` で行えます。

# コンストラクタ

```
ProductGroupOperation(o::AbstractGroupOperation...)
×(o::AbstractGroupOperation...) = ProductGroupOperation(o...)
```
