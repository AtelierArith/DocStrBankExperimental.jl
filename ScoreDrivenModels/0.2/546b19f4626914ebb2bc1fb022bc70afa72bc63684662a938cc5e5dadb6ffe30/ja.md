```
BetaFourParameters
```

  * パラメータ化 a, c, \alpha, \beta
  * スコア
  * フィッシャー情報
  * `time_varying_params` マップ。
  * デフォルトリンク

現在、BetaFourParametersモデルを推定する際には、パラメータaとcを固定することが推奨されています。以下のコードを使用してください：

```julia
gas_beta_4 = ScoreDrivenModel([1, 2, 11, 12], [1, 2, 11, 12], BetaFourParameters, 0.0; time_varying_params=[3])
gas_beta_4.ω[1] = minimum(y) - 0.1*std(y) # パラメータ a
gas_beta_4.ω[2] = maximum(y) + 0.1*std(y) # パラメータ c
```

このコードは、aおよびcパラメータを推定するための単純であまり正確ではないヒューリスティックです。最大尤度法を使用して推定した場合、より良い結果が得られるでしょう。

この事象は、最適化中に勾配が `c < maximum(y)` または `a > minimum(y)` になると、yがBetaFourParameters分布から来ることが不可能になり、DomainErrorsが発生するためです。
