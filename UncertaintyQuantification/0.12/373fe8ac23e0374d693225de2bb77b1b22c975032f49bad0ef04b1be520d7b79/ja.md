```
bayesianupdating(likelihood, models, pointestimate; prior)
```

与えられた `likelihood`、`models` および任意の点推定手法 [`AbstractBayesianPointEstimate`](@ref) を使用してベイズ更新を実行します。

### 注意事項

メソッドは空のモデルのベクターで呼び出すことができます。すなわち、

```
bayesianupdating(likelihood, [], pointestimate)
```

`prior` が指定されていない場合、メソッドは `AbstractBayesianPointEstimate.prior` で指定された事前分布から事前分布を構築します。

`likelihood` はサンプルの `DataFrame` に基づいて定義されなければならず、`DataFrame` の各行に対して尤度を評価する必要があります。

例えば、'Data' を使用した正規分布に基づく対数尤度は次のようになります。

```julia
likelihood(df) = [sum(logpdf.(Normal.(df_i.x, 1), Data)) for df_i in eachrow(df)]
```

尤度を評価するためにモデル評価が必要な場合、`bayesianupdating` に `UQModel` のベクターを渡す必要があります。例えば、上記の変数 `x` が数値モデルの出力である場合です。

関数の一般的な概要については、[`bayesianupdating`](@ref) を参照してください。
