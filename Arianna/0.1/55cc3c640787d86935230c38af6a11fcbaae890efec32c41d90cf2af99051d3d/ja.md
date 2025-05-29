```
mc_step!(system::AriannaSystem, action::Action, policy::Policy, parameters::AbstractArray{T}, rng) where {T<:AbstractFloat}
```

単一のモンテカルロステップを実行します。

# 引数

  * `system`: 修正するシステム
  * `action`: 実行するアクション
  * `policy`: 提案に使用されるポリシー
  * `parameters`: ポリシーのパラメータ
  * `rng`: 擬似乱数生成器
