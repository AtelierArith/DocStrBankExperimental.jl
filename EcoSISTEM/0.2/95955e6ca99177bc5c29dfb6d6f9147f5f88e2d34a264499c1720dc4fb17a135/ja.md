```
ContinuousEvolve(val::Union{Float64, Unitful.Quantity{Float64}}, var::Union{Float64, Unitful.Quantity{Float64}}, tree::BinaryTree)
```

バイナリツリー `tree` に沿ってブラウン運動を介して連続的な特性を進化させる関数です。開始値 `val` と分散 `var` を受け取ります。
