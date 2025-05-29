```
LowRankMatPol(lambda::Vector, vs::Vector{Vector}[, ws::Vector{Vector}])
```

行列 $∑_i λ_i v_i w_i^{\sf T}$ で、$v_i$ は `vs` のエントリ、$w_i$ は `ws` のエントリです。

`ws` が指定されていない場合、`ws = vs` を使用します。
