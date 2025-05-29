```
QuantityArray(::AbstractQuantityArray, ::InternalUnits)
QuantityArray(::AbstractQuantityArray)
```

任意の `AbstractQuantityArray` の実装から物理量を用いて `QuantityArray` を構築します。

`InternalUnits` が指定されていない場合、可能であれば `AbstractQuantityArray` から推測されます。そうでない場合は、基本的な SI 単位が使用されます。
