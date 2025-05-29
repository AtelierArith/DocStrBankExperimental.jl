```julia
struct Kerr{T} <: Krang.AbstractMetric
```

ボイヤー・リンカリスト座標におけるカー計量

  * `mass`: M = 質量
  * `spin`: a = J/M, ここで J は角運動量、M はブラックホールの質量です。
