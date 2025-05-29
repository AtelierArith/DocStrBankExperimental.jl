```
angularMomentumVector(u::AbstractVector{<:Number})
```

カルテシアン状態ベクトルから瞬時の角運動量ベクトルを計算します。

# 引数

-`u::AbstractVector{<:Number}`: カルテシアン状態ベクトル [x; y; z; ẋ; ẏ; ż]。

# 戻り値

-'angular_momentum::Vector{<:Number}': 3次元の角運動量ベクトル。
