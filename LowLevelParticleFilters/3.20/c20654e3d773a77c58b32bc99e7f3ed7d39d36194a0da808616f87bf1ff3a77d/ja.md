```
predict!(kf::SqKalmanFilter, u, p = parameters(kf), t::Real = index(kf); R1 = get_mat(kf.R1, kf.x, u, p, t), α = kf.α)
```

平方根カルマンフィルタの場合、カスタムで提供された `R1` はプロセスノイズの共分散行列の上三角のコレスキー因子でなければなりません。
