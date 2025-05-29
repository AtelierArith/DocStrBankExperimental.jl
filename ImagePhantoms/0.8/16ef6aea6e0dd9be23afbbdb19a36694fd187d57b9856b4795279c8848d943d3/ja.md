```
cone(cx, cy, cz, wx, wy, wz, Φ, Θ, value::Number)
cone(center::NTuple{3,RealU}, width::NTuple{3,RealU}, angle::NTuple{3,RealU}, v)
```

パラメータから `Object{Cone}` を構築します。ここで `width` は `wx` と `wy` の基底半径であり、`wz` は高さです。
