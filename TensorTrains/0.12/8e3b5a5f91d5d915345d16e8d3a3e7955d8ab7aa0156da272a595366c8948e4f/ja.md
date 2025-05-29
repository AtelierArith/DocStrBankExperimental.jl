```
orthogonalize_left!(A::AbstractTensorTrain; svd_trunc::SVDTrunc)
```

SVD分解を用いて、`A`を左直交形式に変換します。

オプションで、`SVDTrunc`を渡すことで切り捨てを行うことができます。
