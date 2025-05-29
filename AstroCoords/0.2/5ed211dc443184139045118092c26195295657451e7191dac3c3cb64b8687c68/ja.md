```
Delaunay{T} <: AstroCoord
```

デローニー軌道要素。軌道の6次元パラメータ化。 L - 標準ケプラーエネルギー G - 標準総角運動量 H - 標準法線角運動量（赤道に対して） M - 平均異常 ω - ペリapsisの引数 Ω - 昇交点の右昇交

コンストラクタ Delaunay(L, G, H, M, ω, Ω) Delaunay(X::AbstractVector{<:Number}) Delaunay(X::AstroCoord, μ::Number)
