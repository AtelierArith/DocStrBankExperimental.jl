```
J2EqOE{T} <: AstroCoord
```

修正された春分点軌道要素。軌道の6次元パラメータ化。n - 平均運動 h - 離心率の近地点の経度への投影 k - 離心率の垂直な近地点の経度への投影 p - 半傾斜のRAANへの投影 q - 半傾斜の垂直なRAANへの投影 L - 真の経度

コンストラクタ J2EqOE(n, h, k, p, q, L) J2EqOE(X::AbstractArray) J2EqOE(X::AstroCoord, μ::Number)
