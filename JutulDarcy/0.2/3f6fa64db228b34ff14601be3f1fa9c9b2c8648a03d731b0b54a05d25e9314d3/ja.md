```
KValueWrapper(K; dependence::Symbol = :pT)
```

K値フラッシュで使用するためのK値補間器のラッパーを作成します。

このラッパーの主な目的は、一般的なフラッシュ条件のNamedTupleを多重線形補間のための正しい引数に変換することです。
