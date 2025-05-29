```
inUnitsOf(quantity::AbstractQuantity, unit::AbstractUnit)::SimpleQuantity
```

`quantity`を`unit`で指定された単位に関して`SimpleQuantity`型のオブジェクトとして表現します。

# 例外を発生させる

  * `Alicorn.Exceptions.DimensionMismatchError`: `quantity`と`unit`の次元が一致しない場合
