```
measure(filter::ExtendedKalmanFilter, bp::GaussianBelief, y::AbstractVector;
    u::AbstractVector = [false])
```

拡張カルマンフィルタを使用して、測定ベクトルyが与えられた予測ガウス信念bpに対して測定更新を実行します。uが指定され、filter.o.Dが宣言されている場合、行列Dはyの予測に因子分解されます。
