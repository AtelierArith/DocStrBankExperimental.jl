```
ADADelta(ρ = 0.9)
```

[ADADelta](https://arxiv.org/abs/1212.5701) は、過去の勾配更新のウィンドウに基づいて学習率を適応させるADAGradのバージョンです。パラメータの調整は必要ありません。

# パラメータ

  * Rho (`ρ`): 各タイムステップで勾配が減衰する係数。

# 例

```julia
opt = ADADelta()
opt = ADADelta(0.89)
```
