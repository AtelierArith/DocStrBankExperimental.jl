```
cross_vector(M::SMatrix) -> SVector
```

行列 `M` を取り、行列の反対称部分から対応する軸ベクトル `v` を形成します ($M_a = (M-M^{T})/2$)。これにより、$v \times w$ は $M_a\cdot w$ と同等になります。
