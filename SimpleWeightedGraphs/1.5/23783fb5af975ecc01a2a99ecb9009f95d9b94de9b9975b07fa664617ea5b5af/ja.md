```
Graphs.adjacency_matrix(g, T; dir)
```

重み付き隣接行列を構築し、要素型 `T` で埋め、エッジの方向 `dir ∈ [:in, :out, :both]` を考慮します（デフォルトは `:out` です）。
