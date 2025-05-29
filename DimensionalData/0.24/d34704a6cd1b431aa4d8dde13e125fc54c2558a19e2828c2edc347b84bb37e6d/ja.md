```
reorder(A::AbstractDimArray, order::Pair) => AbstractDimArray
reorder(A::Dimension, order::Order) => AbstractDimArray
```

すべての次元インデックス/配列を `order` に再配置するか、指定された次元のインデックスをラップされた `Order` に再配置します。

`order` は [`Order`](@ref) であるか、`Dimension => Order` のペアであることができます。

軸の反転が必要ない場合、同じオブジェクトが返され、割り当ては行われません。
