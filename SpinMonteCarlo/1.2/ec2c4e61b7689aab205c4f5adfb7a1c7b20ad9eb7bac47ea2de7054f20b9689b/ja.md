```
gen_snapshot!(model, T, [N=1])
```

スナップショット（スピン配置）を生成して返します。

# 引数

  * `model::Model` : モデル
  * `T::Real` : 温度
  * `N::Integer=1` : 生成されるスナップショットの数
  * `MCS::Integer=8192` : スナップショット生成に続くモンテカルロステップの数
