```
predict(filter::KalmanFilter, b0::GaussianBelief, u::AbstractVector)
```

カルマンフィルタを使用して、制御ベクトルuを考慮してガウス信念b0に対して予測ステップを実行します。
