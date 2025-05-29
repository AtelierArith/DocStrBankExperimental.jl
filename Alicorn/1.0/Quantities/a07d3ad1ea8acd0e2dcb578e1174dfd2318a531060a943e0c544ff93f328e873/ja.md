```
valueInUnitsOf(qArray::AbstractQuantityArray, unit::AbstractUnit)
```

`qArray`を`unit`の単位で表現した数値を返します。

# 例外を発生させる

  * `Alicorn.Exceptions.DimensionMismatchError`: `quantity`と`unit`の次元が一致しない場合
