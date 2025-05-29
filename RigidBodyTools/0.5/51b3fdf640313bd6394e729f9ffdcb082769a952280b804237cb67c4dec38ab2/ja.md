```
cross_matrix(v::SVector) -> SMatrix
```

ベクトル `v` を取り、対応する外積行列 `M` を形成します。これにより、$v \times w$ は $M\cdot w$ と同等になります。
