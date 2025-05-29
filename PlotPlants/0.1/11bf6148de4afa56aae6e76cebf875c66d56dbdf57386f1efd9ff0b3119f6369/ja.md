```
mutable struct LinearRegressionResult
```

# フィールド

  * `lm::Any`: 回帰結果
  * `r2::Number`: 調整済みR二乗
  * `inter::Number`: フィッティングの切片
  * `slope::Number`: フィッティングの傾き
  * `inter_p::Number`: 切片のP値
  * `slope_p::Number`: 傾きのP値
  * `inter_ci::Array`: 切片の信頼区間
  * `slope_ci::Array`: 傾きの信頼区間
  * `df::DataFrames.DataFrame`: 予測データフレーム
