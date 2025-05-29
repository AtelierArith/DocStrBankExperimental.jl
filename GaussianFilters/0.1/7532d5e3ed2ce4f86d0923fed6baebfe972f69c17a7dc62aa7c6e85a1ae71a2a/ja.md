```
measure(filter::UnscentedKalmanFilter, bp::GaussianBelief, y::AbstractVector;
    u::AbstractVector = [false])
```

予測されたガウス信念 bp に対して、測定ベクトル y を考慮して測定更新を実行するために、無香カールマンフィルタを使用します。u が指定され、filter.o.D が宣言されている場合、行列 D は y の予測に因数分解されます。
