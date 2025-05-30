```
RectSearchSpace(dimranges::AbstractVector; [dimdigits = nothing])
```

指定された各次元の有効値の範囲と、指定されている場合は各次元の`dimdigits`精度を持つ`RectSearchSpace`を作成します。指定された精度を持つ次元が少なくとも1つある場合は`MixedPrecisionRectSearchSpace`を返し、そうでない場合は`ContinuousRectSearchSpace`を返します。
