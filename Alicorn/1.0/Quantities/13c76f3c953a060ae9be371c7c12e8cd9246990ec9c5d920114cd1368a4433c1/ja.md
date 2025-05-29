```
inInternalUnitsOf(quantity::Quantity{T}, targetIntU::InternalUnits) where T
```

`quantity`に対応する新しい`Quantity{S}`を返しますが、`targetIntU`を新しい内部単位として使用して保存されます。

返される量の値の型`S`は、可能であれば`T`と同一です。
