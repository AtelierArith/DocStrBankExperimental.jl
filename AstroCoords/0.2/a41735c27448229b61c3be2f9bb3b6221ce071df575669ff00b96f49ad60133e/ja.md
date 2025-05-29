```
Keplerian{T} <: AstroCoord
```

ケプラー軌道要素。軌道の6次元パラメータ化。a - 半長軸 e - 離心率 i - 傾斜角 Ω - 昇交点の赤経 ω - ペリジーの引数 f - 真異常

コンストラクタ Keplerian(a, e, i, Ω, ω, f) Keplerian(X::AbstractArray) Keplerian(X::AstroCoord, μ::Number)
