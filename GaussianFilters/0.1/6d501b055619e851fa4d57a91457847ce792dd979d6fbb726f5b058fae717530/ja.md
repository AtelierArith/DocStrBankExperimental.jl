```
measure(filter::KalmanFilter, bp::GaussianBelief, y::AbstractVector;
    u::AbstractVector = [false])
```

カルマンフィルタを使用して、測定ベクトルyが与えられたときに予測されたガウス信念bpに対して測定更新を実行します。uが指定され、filter.o.Dが宣言されている場合、行列Dはyの予測に因数分解されます。
