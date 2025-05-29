```
project(M::HeisenbergGroup, p, X)
```

行列 `X` をユークリッド埋め込みからリー代数 [`HeisenbergGroup`](@ref) `M` に射影します。対角要素を 0 に設定し、最初の行と最後の列を除くすべての非対角要素を 0 に設定します。
