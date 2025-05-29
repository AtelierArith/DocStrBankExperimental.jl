```
bayesianupdating(prior, likelihood, models, mcmc)
```

与えられた `prior`、`likelihood`、`models` および任意の MCMC サンプラー [`AbstractBayesianMethod`](@ref) を使用してベイズ更新を実行します。

また、`models` を指定せずにメソッドを呼び出すこともできます。

```
bayesianupdating(prior, likelihood, mcmc)
```

[`TransitionalMarkovChainMonteCarlo`](@ref) を使用する場合、`prior` は自動的に構築されます。

```
bayesinupdating(likelihood, models, tmcmc)
bayesianupdating(likelihood, tmcmc)
```

### 注意事項

`likelihood` は `DataFrame` のサンプルに基づいて定義されなければならない Julia 関数であり、`DataFrame` の各行に対して尤度を評価する必要があります。

例えば、'Data' を使用した正規分布に基づく対数尤度は次のようになります。

```julia
likelihood(df) = [sum(logpdf.(Normal.(df_i.x, 1), Data)) for df_i in eachrow(df)]
```

尤度を評価するためにモデル評価が必要な場合、`bayesianupdating` に `UQModel` のベクトルを渡す必要があります。例えば、上記の変数 `x` が数値モデルの出力である場合です。
