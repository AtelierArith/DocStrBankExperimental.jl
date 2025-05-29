```
RectSearchSpace(dimranges::AbstractVector; [dimdigits = nothing])
```

指定された各次元の有効値の範囲と、指定された場合は各次元の`dimdigits`精度を持つ`RectSearchSpace`を作成します。少なくとも1つの次元に指定された精度がある場合（dimdigits[i] ≥ 0）、`MixedPrecisionRectSearchSpace`を返し、そうでなければ`ContinuousRectSearchSpace`を返します。
