```
valueOfDimensionless(quantity::AbstractQuantity)
```

次元のない量から単位を取り除き、その生の値を返します。

# 例外を発生させる

  * `Alicorn.Exceptions.DimensionMismatchError`: `quantity` が次元のないものでない場合
