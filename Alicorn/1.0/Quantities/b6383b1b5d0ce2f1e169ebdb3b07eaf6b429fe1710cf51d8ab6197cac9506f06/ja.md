```
valueOfDimensionless(qArray::AbstractQuantityArray)
```

次元のない量の配列から単位を取り除き、その値を返します。

# 例外を発生させる

  * `Alicorn.Exceptions.DimensionMismatchError`: `qArray` が次元を持たない場合
