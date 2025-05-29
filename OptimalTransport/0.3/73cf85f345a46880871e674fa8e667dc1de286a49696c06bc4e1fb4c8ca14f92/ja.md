```
SinkhornStabilized(; absorb_tol::Real=1_000)
```

エントロピー正則化最適輸送問題を解くための吸収許容度 `absorb_tol` を持つ対数領域安定化Sinkhornアルゴリズムを構築します。

# 参考文献

Schmitzer, B. (2019). [Stabilized Sparse Scaling Algorithms for Entropy Regularized Transport Problems](https://doi.org/10.1137/16m1106018). SIAM Journal on Scientific Computing, 41(3), A1443–A1481.
