```
summarizeEstimates(samples)
summarizeEstimates(samples; savetofile="ite_samples.csv")
```

予測された推定値の要約（反事実的結果または個別治療効果）

[`sampleITE`](@ref) または [`predictCounterfactualEffects`](@ref) からのサンプルの平均、下限および上限の分位数のデータフレームを作成します。

パラメータ：

  * `samples`: sampleSATE または sampleITE からの `n x m` 配列のサンプル
  * `savetofile::String`: 結果のデータフレームをCSVとして渡されたファイル名に保存するオプション
  * `credible_interval::Float64`: [0,1] の実数で、0.90 は90%の信頼区間のデフォルトです

戻り値：

  * `df`: サンプルの周りの信頼区間のための個別、平均、下限、および上限の値のデータフレーム。
