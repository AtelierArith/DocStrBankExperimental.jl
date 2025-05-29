```
PeriodicSymbolicMatrix(F, T; nperiod = k) -> A::PeriodicSymbolicMatrix
```

連続時間周期的記号行列の表現。

連続時間周期的記号行列オブジェクト `A` は、記号実行列または記号変数 `t` のベクトルである `F`、関連する時間周期 `T`、およびキーワード引数 `nperiod = k` を介して指定された関連するサブ周期の数から構築されます。任意の実時間値 `t` に対して `F(t) = F(t+T/k)` であると仮定されます。記号行列 `F`、周期 `T`、およびサブ周期の数 `k` は、それぞれ `A.F`、`A.period`、および `A.nperiod` を介してアクセスできます。
