```
rotate(data, yaw::Number, center::PVector; vel::Bool = true)
```

データ内のすべての粒子を中心点を中心にラジアンのオイラー角 (α, β, γ) = (ロール, ピッチ, ヨー) で回転させます。

  * `vel::Bool = false`: 同時に原点周りの速度も回転させます。
