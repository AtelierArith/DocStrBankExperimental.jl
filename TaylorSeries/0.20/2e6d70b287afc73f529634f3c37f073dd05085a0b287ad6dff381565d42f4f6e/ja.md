```
taylor_expand(f, x0; order)
```

関数 `f` のテイラー展開を点 `x0` の周りで計算します。

`x0` がスカラーの場合、`Taylor1` 展開が返されます。`x0` がベクトルの場合、`TaylorN` 展開が計算されます。`x0` の次元（`length(x0)`）が `TaylorN` に設定された変数の数（`get_numvars()`）と異なる場合、`AssertionError` がスローされます。
