```
cor(d::StateSpaceSet) → m::SMatrix
```

`d`の列から相関行列`m`を計算します。ここで、`m[i, j]`は`d[:, i]`と`d[:, j]`の相関を表します。
