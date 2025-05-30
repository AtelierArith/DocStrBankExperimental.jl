```
JuMP.list_of_constraint_types(model::AbstractSpGpModel) -> Vector{Tuple{DataType,DataType}}
```

モデル内の制約タイプのリストを (function*type, set*type) タプルとして返します。

# 返り値

  * 各タプルが制約の関数タイプとセットタイプを含むタプルのベクター
