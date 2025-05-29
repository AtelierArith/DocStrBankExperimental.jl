```
cov(d::StateSpaceSet) → m::SMatrix
```

`d`の列から共分散行列`m`を計算します。ここで、`m[i, j]`は`d[:, i]`と`d[:, j]`の間の共分散です。
