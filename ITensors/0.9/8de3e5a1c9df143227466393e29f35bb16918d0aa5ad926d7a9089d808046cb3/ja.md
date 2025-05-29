```
diag_itensor([::Type{ElT} = Float64, ]inds)
diag_itensor([::Type{ElT} = Float64, ]inds::Index...)
```

要素型 `ElT` のスパース ITensor を作成し、対角線上にのみ要素を格納します。デフォルトでは、対角線上に `zero(T)` が配置されます。

ストレージは `NDTensors.Diag` 型になります。
