```
Milankovich{T} <: AstroCoord
```

ミランコビッチ軌道要素。軌道の7次元パラメータ化。 hx - 角運動量ベクトルのX成分 hy - 角運動量ベクトルのY成分 hz - 角運動量ベクトルのZ成分 ex - 離心率ベクトルのX成分 ey - 離心率ベクトルのY成分 ez - 離心率ベクトルのZ成分 L - 真経度

コンストラクタ Milankovich(hx, hy, hz, ex, ey, ez, L) Milankovich(X::AbstractArray) Milankovich(X::AstroCoord, μ::Number)
