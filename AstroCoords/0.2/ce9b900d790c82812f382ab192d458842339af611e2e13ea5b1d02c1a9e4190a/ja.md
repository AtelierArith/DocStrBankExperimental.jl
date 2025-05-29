```
angularMomentumVector(X::AstroCoord, μ::Number)
```

直交座標状態ベクトルから瞬時の角運動量ベクトルを計算します。

# 引数

-`X::AstroCoord`: 軌道を記述する座標セット。 -`μ::Number`: 中心天体の標準重力パラメータ。

# 戻り値

-`angular_momentum::Vector{<:Number}`: 3次元角運動量ベクトル。
