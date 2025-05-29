```
predict(filter::UnscentedKalmanFilter, b0::GaussianBelief, u::AbstractVector)
```

制御ベクトル u が与えられたとき、ガウス信念 b0 に対して予測ステップを実行するために無香カールマンフィルタを使用します。
