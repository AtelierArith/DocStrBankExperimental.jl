```
valueInUnitsOf(quantity::AbstractQuantity, simpleQuantity::SimpleQuantity)
```

`quantity`を`simpleQuantity`の単位で表した数値を返します。

結果は`valueOfDimensionless(quantity / simpleQuantity)`と同等です。

# 例外を発生させる

  * `Alicorn.Exceptions.DimensionMismatchError`: `quantity`と`simpleQuantity`の次元が一致しない場合
