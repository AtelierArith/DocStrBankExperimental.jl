```
Normalize(lb, ub)
```

入力に対して `(x - lb) / (ub - lb)` に基づいて最小-最大スケーリングを実行します。 `lb` と `ub` の長さは入力ベクトルと一致する必要があります。

# 引数:

  * `lb`: 下限、デフォルト = zero(ub)。
  * `ub`: 上限。
