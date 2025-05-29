```
exit_rate(Q)
```

# 説明

```
生成行列 Q を出口確率 E とレート R に分解します。すなわち、Q = ER
```

# 引数

  * `Q::Matrix`: 生成行列または遷移行列。

# 戻り値

  * (; exit_probabilities, rates)::NamedTuple: 生成行列の出口確率とレート。
