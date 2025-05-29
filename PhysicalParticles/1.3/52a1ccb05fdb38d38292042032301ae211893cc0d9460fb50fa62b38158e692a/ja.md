```
rotate(data::Array, vec::PVector, θ::Number; vel::Bool = true)
```

データ内のすべての粒子を方向ベクトル `vec` の周りに角度 `θ` だけ回転させます。

  * `vel::Bool = false`: 同時に原点の周りに速度を回転させます。
