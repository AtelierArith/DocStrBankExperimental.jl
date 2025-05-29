```
PeriodicFunctionMatrix(f, T; nperiod = k) -> A::PeriodicFunctionMatrix
```

連続時間周期関数行列の表現。

連続時間周期関数行列オブジェクト `A` は、実数時間変数 `t` の実数行列関数 `f(t)`、関連する時間周期 `T`、およびキーワード引数 `nperiod = k` を介して指定された関連するサブ周期の数から構築されます。任意の実時間値 `t` に対して `f(t) = f(t+T/k)` であると仮定されます。関数 `f(t)`、周期 `T`、`f(t)` の行と列の次元、サブ周期の数 `k` は、それぞれ `A.f`、`A.period`、タプル `A.dims` および `A.nperiod` を介してアクセスできます。
