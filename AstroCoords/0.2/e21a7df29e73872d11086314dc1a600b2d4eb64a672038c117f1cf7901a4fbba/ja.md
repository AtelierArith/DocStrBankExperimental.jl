```
angularMomentumQuantity(u::AbstractVector{<:Number})
```

瞬時角運動量を計算します。

# 引数

-`u::AbstractVector{<:Number}`: カルテシアン状態ベクトル [x; y; z; ẋ; ẏ; ż]。

# 戻り値

-`angular_momentum::Number`: 物体の角運動量。
