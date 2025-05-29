```
project(M::HeisenbergGroup, p)
```

ユークリッド埋め込みの行列 `p` を [`HeisenbergGroup`](@ref) `M` に射影します。対角要素を 1 に設定し、最初の行と最後の列を除くすべての非対角要素を 0 に設定します。
