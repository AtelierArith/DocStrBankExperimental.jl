```
Graphs.laplacian_matrix(g, T; dir)
```

隣接行列から次数行列を引きます。両方とも要素型 `T` で埋められ、エッジの方向 `dir ∈ [:in, :out, :both]` を考慮します（Graphs.jl とは異なり、デフォルトは `:out` です）。
