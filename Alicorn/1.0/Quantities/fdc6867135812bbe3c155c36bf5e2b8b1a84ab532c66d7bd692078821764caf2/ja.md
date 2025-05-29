```
Quantity(::AbstractQuantity, ::InternalUnits)
Quantity(::AbstractQuantity)
```

任意の `AbstractQuantity` の実装から物理量を用いて `Quantity` を構築します。

`InternalUnits` が指定されていない場合、基本的な SI 単位を使用して構築されます。
