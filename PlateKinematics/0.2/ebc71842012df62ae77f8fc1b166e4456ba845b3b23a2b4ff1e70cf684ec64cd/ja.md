```julia
struct FiniteRotSph
```

球面座標における有限回転、度数で表現されます。

## フィールド

  * `Lon::Float64`: 回転軸の経度（度-東）
  * `Lat::Float64`: 回転軸の緯度（度-北）
  * `Angle::Float64`: 回転角（度）
  * `Time::Union{Float64, Nothing}`: 回転の年齢（百万年）
  * `Covariance::Covariance`: [`Covariance`](@ref)（ラジアン²）

## 例:

```julia-repl
julia> PlateKinematics.FiniteRotSph(30, 20, 10)
PlateKinematics.FiniteRotSph:
        Lon        : 30.0
        Lat        : 20.0
        Angle      : 10.0
        Time       : nothing
        Covariance : PlateKinematics.Covariance(0.0, 0.0, 0.0, 0.0, 0.0, 0.0)

julia> array = [30, 20, 10];
julia> PlateKinematics.FiniteRotSph(array)
PlateKinematics.FiniteRotSph:
        Lon        : 30.0
        Lat        : 20.0
        Angle      : 10.0
        Time       : nothing
        Covariance : PlateKinematics.Covariance(0.0, 0.0, 0.0, 0.0, 0.0, 0.0)

julia> PlateKinematics.FiniteRotSph(30, 20, 10, 2)
PlateKinematics.FiniteRotSph:
        Lon        : 30.0
        Lat        : 20.0
        Angle      : 10.0
        Time       : 2.0
        Covariance : PlateKinematics.Covariance(0.0, 0.0, 0.0, 0.0, 0.0, 0.0)

julia> array = [1, 2, 3, 4, 5, 6];
julia> PlateKinematics.FiniteRotSph(30, 20, 10, array)
PlateKinematics.FiniteRotSph(30, 20, 10, nothing, PlateKinematics.Covariance(1, 2, 3, 4, 5, 6))

julia> array = [1, 2, 3, 4, 5, 6];
julia> PlateKinematics.FiniteRotSph(30, 20, 10, 2, array)
PlateKinematics.FiniteRotSph:
        Lon        : 30.0
        Lat        : 20.0
        Angle      : 10.0
        Time       : 2.0
        Covariance : PlateKinematics.Covariance(1.0, 2.0, 3.0, 4.0, 5.0, 6.0)
```
