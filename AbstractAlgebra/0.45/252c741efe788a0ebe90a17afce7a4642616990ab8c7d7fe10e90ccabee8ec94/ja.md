```
is_alternating(M::MatrixElem)
```

行列 `M` に対応する形式が交互であるかどうかを返します。すなわち、`M = -transpose(M)` であり、`M` の対角線上にゼロがある必要があります。`M` が正方行列でない場合は `false` を返します。
