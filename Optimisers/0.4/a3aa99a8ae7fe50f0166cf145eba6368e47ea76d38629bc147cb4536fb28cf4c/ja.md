```
AdaDelta(ρ = 0.9, ϵ = 1e-8)
AdaDelta(; [rho, epsilon])
```

[AdaDelta](https://arxiv.org/abs/1212.5701)は、過去の勾配更新のウィンドウに基づいて学習率を調整するAdaGradのバージョンです。パラメータの調整は必要ありません。

# パラメータ

  * Rho (`ρ == rho`): 各タイムステップで勾配が減衰する係数。
  * Machine epsilon (`ϵ == epsilon`): ゼロ除算を防ぐための定数（デフォルトを変更する必要はありません）
