```
degree_matrix(g, T; dir)
```

重み付き対角度行列を構築し、要素タイプ `T` で埋め、エッジの方向 `dir ∈ [:in, :out, :both]` を考慮します（デフォルトは `:out` です）。
