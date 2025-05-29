```
MLEControl(init::parameter, optimizer::String, ci::Bool, maxEval::Int64)
```

推定設定のための構造体。

  * `init`: 最適化の初期値
  * `optimizer`: 最適化ルーチン、"NelderMead"、"BFGS" または "LBFGS"
  * `ci`: 指標: 信頼区間を計算するべきか？
  * `maxEval`: 最大尤度評価回数
