```
grad_neg_abs_sum_free_kurt(W, Y)
```

この関数は、neg*abs*sum*free*kurt(W'*Y) の W に関する勾配を計算します。

# 引数

  * `W`: size(`W`, 1) = size(`Y`, 1) である行列
  * `Y`: 同じ型および同じ次元の行列の配列

# 出力

  * `grad`: neg*abs*sum*free*kurt(W'*Y) の W に関する勾配
