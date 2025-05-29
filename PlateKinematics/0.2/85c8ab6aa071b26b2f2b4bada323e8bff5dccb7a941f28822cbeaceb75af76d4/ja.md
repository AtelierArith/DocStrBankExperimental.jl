```julia
struct FiniteRotCart
```

有限回転をデカルト座標系で、度数法で表現します。

## フィールド

  * `X::Float64`: 度数法でのX座標
  * `Y::Float64`: 度数法でのY座標
  * `Z::Float64`: 度数法でのZ座標
  * `TimeRange::Union{Float64, Nothing}`: 回転の年齢（百万年単位）
  * `Covariance::Covariance`: [`Covariance`](@ref)（ラジアン²）

## 例:

```julia-repl
julia> PlateKinematics.FiniteRotCart(1, 2, 3)
PlateKinematics.FiniteRotCart:
        X          : 1.0
        Y          : 2.0
        Z          : 3.0
        Time       : nothing
        Covariance : PlateKinematics.Covariance(0.0, 0.0, 0.0, 0.0, 0.0, 0.0)

julia> array = [30, 20, 10];
julia> PlateKinematics.FiniteRotCart(array)
PlateKinematics.FiniteRotCart:
        X          : 30.0
        Y          : 20.0
        Z          : 10.0
        Time       : nothing
        Covariance : PlateKinematics.Covariance(0.0, 0.0, 0.0, 0.0, 0.0, 0.0)

julia> PlateKinematics.FiniteRotCart(1, 2, 3, 1.5)
PlateKinematics.FiniteRotCart:
        X          : 1.0
        Y          : 2.0
        Z          : 3.0
        Time       : 1.5
        Covariance : PlateKinematics.Covariance(0.0, 0.0, 0.0, 0.0, 0.0, 0.0)

julia> array = [1, 2, 3, 4, 5, 6];
julia> PlateKinematics.FiniteRotCart(30, 20, 10, array)
PlateKinematics.FiniteRotCart:
        X          : 30.0
        Y          : 20.0
        Z          : 10.0
        Time       : nothing
        Covariance : PlateKinematics.Covariance(1.0, 2.0, 3.0, 4.0, 5.0, 6.0)

julia> array = [1, 2, 3, 4, 5, 6];
julia> PlateKinematics.FiniteRotCart(1, 2, 3, 1.5, array)
PlateKinematics.FiniteRotCart:
        X          : 1.0
        Y          : 2.0
        Z          : 3.0
        Time       : 1.5
        Covariance : PlateKinematics.Covariance(1.0, 2.0, 3.0, 4.0, 5.0, 6.0)
```
