```
LogitDynamics(g, beta)
```

`LogitDynamics` インスタンスを構築します。

# 引数

  * `g::NormalFormGame{N,T}` : `NormalFormGame` インスタンス。
  * `beta::S` : プレイヤーの意思決定におけるノイズのレベル。

# 戻り値

  * `::LogitDynamics` : Logit-Dynamics モデル。
