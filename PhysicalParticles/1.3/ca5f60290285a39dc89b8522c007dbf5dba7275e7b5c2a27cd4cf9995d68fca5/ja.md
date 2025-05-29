```
rotate(data, yaw::Number, center::PVector; vel::Bool = true)
```

データ内のすべての粒子をラジアンのオイラー角 (α, β, γ) = (ロール, ピッチ, ヤー) で回転させます。

  * `vel::Bool = false`: 同時に原点周りの速度も回転させます。
