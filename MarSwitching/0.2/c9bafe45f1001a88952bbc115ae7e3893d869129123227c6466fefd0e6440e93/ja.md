```
smoothed_probs(model::MSM; kwargs...)
```

各時間帯における各状態の平滑化された確率を返します（Kim, 1994）。MSMモデルのみが提供されている場合、インサンプルデータが使用されます。

平滑化された確率は、フィルタリングされた確率とは異なり、利用可能なすべてのデータを使用して計算されます。

# 引数

  * `model::MSM`: 推定されたモデル。
  * `y`: 従属変数のためのオプションデータ。
  * `exog_vars`: モデルの非スイッチング部分のためのオプションの外生変数。
  * `exog_switching_vars`: モデルのスイッチング部分のためのオプションの外生変数。
  * `exog_tvtp`: モデルのtvtp部分のためのオプションの外生変数。

[`filtered_probs`](@ref)および[`expected_duration`](@ref)も参照してください。

# 参考文献

Kim, Chang Jin (1994). Dynamic Linear Models with Markov-Switching. Journal of Econometrics 60, 1-22.
