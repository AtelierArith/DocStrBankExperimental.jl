```
orthogonalize_right!(A::AbstractTensorTrain; svd_trunc::SVDTrunc)
```

`A`をSVD分解を用いて右直交形式に変換します。

オプションで、`SVDTrunc`を渡すことで切り捨てを行うことができます。
