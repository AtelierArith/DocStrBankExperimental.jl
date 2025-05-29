```
rotate(data, vec::PVector, θ::Number, center::PVector; vel::Bool = true)
```

中心点`center`の周りで、方向ベクトル`vec`に沿って角度`θ`だけデータ内のすべての粒子を回転させます。

  * `vel::Bool = false`: 同時に原点の周りで速度も回転させます。
