```julia
struct EulerVectorSph
```

球面座標系におけるオイラーベクトルで、以下のパラメータを持ちます：

## フィールド

  * `Lon::Float64`: オイラー極の経度（度-東）
  * `Lat::Float64`: オイラー極の緯度（度-北）
  * `AngVelocity::Float64`: 角速度（度/Myr）
  * `TimeRange::Union{Matrix, Nothing}`: 回転の初期から最終年齢
  * `Covariance::Covariance`: [`Covariance`](@ref)（ラジアン²/Myr²）

## 例：

```julia-repl
julia> PlateKinematics.EulerVectorSph(1, 2, 3)
PlateKinematics.EulerVectorSph:
        Lon         : 1.0
        Lat         : 2.0
        AngVelocity : 3.0
        TimeRange   : nothing
        Covariance  : PlateKinematics.Covariance(0.0, 0.0, 0.0, 0.0, 0.0, 0.0)

julia> array = [30, 20, 10];
julia> PlateKinematics.EulerVectorSph(array)
PlateKinematics.EulerVectorSph:
        Lon         : 30.0
        Lat         : 20.0
        AngVelocity : 10.0
        TimeRange   : nothing
        Covariance  : PlateKinematics.Covariance(0.0, 0.0, 0.0, 0.0, 0.0, 0.0)

julia> array = [1.5 2.5];
julia> length(array) == 2
true
julia> PlateKinematics.EulerVectorSph(30, 20, 10, array)
PlateKinematics.EulerVectorSph:
        Lon         : 30.0
        Lat         : 20.0
        AngVelocity : 10.0
        TimeRange   : [1.5 2.5]
        Covariance  : PlateKinematics.Covariance(0.0, 0.0, 0.0, 0.0, 0.0, 0.0)

julia> array = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0];
julia> length(array) != 2
true
julia> PlateKinematics.EulerVectorSph(30, 20, 10, array)
PlateKinematics.EulerVectorSph:
        Lon         : 30.0
        Lat         : 20.0
        AngVelocity : 10.0
        TimeRange   : nothing
        Covariance  : PlateKinematics.Covariance(1.0, 2.0, 3.0, 4.0, 5.0, 6.0)
```
