```
ModEq{T} <: AstroCoord
```

修正された春分点軌道要素。軌道の6次元パラメータ化。p - 半パラメータ f - 近点経度への偏心率の投影 g - ⟂ 近点経度への偏心率の投影 h - RAANへの半傾斜の投影 k - ⟂ RAANへの半傾斜の投影 L - 真の経度

コンストラクタ ModEq(p, f, g, h, k, l) ModEq(X::AbstractArray) ModEq(X::AstroCoord, μ::Number)
