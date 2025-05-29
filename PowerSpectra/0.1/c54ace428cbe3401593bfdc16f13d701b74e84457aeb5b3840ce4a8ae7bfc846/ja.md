```
CovField(name, maskT, maskP,
    σ²II::HealpixMap{T, O, AA}, σ²QQ::HealpixMap{T, O, AA}, σ²UU::HealpixMap{T, O, AA},
    beamT::SpectralVector{T}, beamP::SpectralVector{T})
```

このフィールドに関する共分散に必要な情報を記述する構造体を作成します。

# 引数:

  * `name::String`: このフィールドの名前
  * `maskT::HealpixMap{T}`: 温度マスク
  * `maskP::HealpixMap{T}`: 偏光マスク
  * `σ²::PolarizedHealpixMap{T}`: ピクセル分散
  * `beamT::SpectralVector{T}`: 温度ビーム
  * `beamP::SpectralVector{T}`: 偏光ビーム
