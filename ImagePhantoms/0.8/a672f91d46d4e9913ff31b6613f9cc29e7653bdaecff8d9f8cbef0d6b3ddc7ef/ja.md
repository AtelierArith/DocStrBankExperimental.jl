```
cylinder(cx, cy, cz, wx, wy, wz, Φ, Θ, value::Number)
cylinder(center::NTuple{3,RealU}, width::NTuple{3,RealU}, angle::NTuple{3,RealU}, v)
```

パラメータから `Object{Cylinder}` を構築します。ここで `width` は x,y の *半径* と z の *高さ* です。
