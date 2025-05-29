```
inUnitsOf(qArray::AbstractQuantityArray, unit::AbstractUnit)::SimpleQuantityArray
```

`qArray`を`unit`で指定された単位に関して`SimpleQuantityArray`型のオブジェクトとして表現します。

# 例外を発生させる

  * `Alicorn.Exceptions.DimensionMismatchError`: `qArray`と`unit`の次元が一致しない場合
