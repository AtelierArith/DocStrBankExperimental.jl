```julia
struct EulerVectorCart
```

ユークリッドベクトルの直交座標系で、度/Myrで表現されます。

## フィールド

  * `X::Float64`: 度/MyrでのX座標
  * `Y::Float64`: 度/MyrでのY座標
  * `Z::Float64`: 度/MyrでのZ座標
  * `TimeRange::Union{Matrix, Nothing}`: 回転の初期から最終の年齢
  * `Covariance::Covariance`: [`Covariance`](@ref) のラジアン²/Myr²での共分散

## 例:

[`EulerVectorSph`](@ref) と同じ外部コンストラクタメソッド。
