```
correct!(kf::SqKalmanFilter, u, y, p = parameters(kf), t::Real = index(kf); R2 = get_mat(kf.R2, kf.x, u, p, t))
```

平方根カルマンフィルタの場合、カスタムで提供された `R2` は、測定ノイズの共分散行列の上三角のコレスキー因子でなければなりません。
