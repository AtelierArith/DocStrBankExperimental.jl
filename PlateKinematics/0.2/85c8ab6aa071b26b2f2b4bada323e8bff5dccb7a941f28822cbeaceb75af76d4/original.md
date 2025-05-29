```julia
struct FiniteRotCart
```

Finite rotation in Cartesian coordinates, expressed in degrees.

## Fields

  * `X::Float64`: X-coordinate in degrees
  * `Y::Float64`: Y-coordinate in degrees
  * `Z::Float64`: Z-coordinate in degrees
  * `TimeRange::Union{Float64, Nothing}`: Age of rotation in million years
  * `Covariance::Covariance`: [`Covariance`](@ref) in radians²

## Examples:

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
