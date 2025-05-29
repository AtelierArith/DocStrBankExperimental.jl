```
gumbelfitpwm(df::DataFrame, datacol::Symbol)::pwmAbstractExtremeValueModel
```

確率加重モーメントを用いてGumbelパラメータを推定します。

ブロック最大値データはデータフレーム`df`の列`datacol`にあります。
