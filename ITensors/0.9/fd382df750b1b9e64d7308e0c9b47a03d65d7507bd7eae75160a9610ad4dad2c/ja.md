```
diag_itensor([ElT::Type, ]x::Number, inds...)
diagitensor([ElT::Type, ]x::Number, inds...)
```

対角線上にのみ非ゼロ要素を持つスパースITensorを作成します。一般に、対角要素は値 `x` に設定され、ITensorの要素タイプは `eltype(x)` になりますが、`ElT` によって明示的に指定されている場合を除きます。ストレージは `NDTensors.Diag` タイプになります。

`x` が `Union{Int, Complex{Int}}` の場合、デフォルトでは `float(x)` に変換されます。この動作は将来的に変更される可能性があることに注意してください。
