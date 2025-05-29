```
linearpredictor(model::RegressionModel)
```

モデルの線形予測子 `Xβ` を返します。ここで `X` はモデル行列、`β` は係数のベクトルです。また、モデルがオフセットでフィットされている場合は `Xβ + offset` を返します。
