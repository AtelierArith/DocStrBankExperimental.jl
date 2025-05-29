```
inInternalUnitsOf(qArray::QuantityArray{T}, targetIntU::InternalUnits) where T
```

`qArray`に対応する新しい`QuantityArray`を返しますが、内部単位として`targetIntU`を使用して保存されます。

返される量の配列の値の型`S`は、可能であれば`T`と同一です。
