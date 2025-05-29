```
SimpleQuantityArray(quantityArray::AbstractQuantityArray)
```

任意の `AbstractQuantityArray` の実装から `SimpleQuantityArray` を構築します。

`quantityArray` が `SimpleQuantityArray` 型の場合は、変更されずに返されます。`quantityArray` が `QuantityArray` 型の場合は、`quantityArray.InternalUnits` で指定されたSI単位で表現されます。
