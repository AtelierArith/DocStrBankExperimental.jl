```
grid_interpolate!(q::Edges{Primal/Dual},dq::EdgeGradient{Primal/Dual})
```

プライマル（デュアル）テンソルデータ `dq` をプライマル（デュアル）エッジ位置に補間し、それを `q` に保持します。
