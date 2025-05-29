decomposition(Q)

# 説明

```
生成行列 Q を可逆で体積を保存する成分に分解します。
```

# 引数

  * `Q::Matrix`: 生成行列または遷移行列。

# 戻り値

  * (; exit_probabilities, rates)::NamedTuple: 生成行列の出口確率とレート。
