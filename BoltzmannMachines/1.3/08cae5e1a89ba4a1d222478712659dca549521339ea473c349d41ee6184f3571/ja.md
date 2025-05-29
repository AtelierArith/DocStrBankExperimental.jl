```
exactloglikelihood(dbm, x)
exactloglikelihood(dbm, x, logz)
```

与えられたデータセット `x` と DBM `dbm` に対して、平均対数尤度を正確に計算します。`dbm` の分配関数の対数の値が引数 `logz` として提供されていない場合、`exactlogpartitionfunction(dbm)` によって計算されます。
