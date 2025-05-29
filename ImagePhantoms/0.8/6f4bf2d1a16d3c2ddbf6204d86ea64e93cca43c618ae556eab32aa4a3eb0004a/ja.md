```
cuboid(cx, cy, cz, wx, wy, wz, Φ, Θ, value::Number)
cuboid(center::NTuple{3,RealU}, width::NTuple{3,RealU}, angle::NTuple{3,RealU}, v)
```

パラメータから `Object{Cuboid}` を構築します。ここで `width` は全幅です。
