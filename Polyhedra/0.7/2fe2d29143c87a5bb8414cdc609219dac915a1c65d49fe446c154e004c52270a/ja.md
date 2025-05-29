```
hrep(model::JuMP.Model)
```

JuMPモデル`model`の実現可能集合からH-表現を構築します。モデルに非線形制約が存在する場合、それらは無視されます。
