```
valueInUnitsOf(quantityArray::AbstractQuantityArray, simpleQuantity::SimpleQuantity)
```

`quantityArray`を`simpleQuantity`の単位で表現した数値を返します。

結果は`valueOfDimensionless(quantityArray / simpleQuantity)`と同等です。

# 例外を発生させる

  * `Alicorn.Exceptions.DimensionMismatchError`: `quantityArray`と`simpleQuantity`の次元が一致しない場合
