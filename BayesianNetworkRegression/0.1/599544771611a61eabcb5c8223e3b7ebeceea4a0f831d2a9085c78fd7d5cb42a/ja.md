```
Summary(results::Results;interval::Int=95,digits::Int=3)
```

結果の要約統計量を生成します：エッジ係数の点推定値と信頼区間、個々のノードの影響の確率

# 引数

  * `results`: [`Fit!`](@ref) を実行して返された Results オブジェクト
  * `interval`: （オプション）整数、信頼区間のレベル。デフォルトは95%。
  * `digits`: （オプション）整数、結果を丸める小数点以下の桁数。デフォルトは3。

# 戻り値

エッジ係数の点推定値の行列（`coef_matrix`）、エッジ係数の信頼区間の行列（`ci_matrix`）、および各ノードの影響の確率を含む DataFrame（`pi_nodes`）を含む BNRSummary オブジェクト。
