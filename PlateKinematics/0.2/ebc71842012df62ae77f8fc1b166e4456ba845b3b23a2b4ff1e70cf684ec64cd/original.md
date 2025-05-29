```julia
struct FiniteRotSph
```

Finite rotation in Spherical coordinates, expressed in degrees.

## Fields

  * `Lon::Float64`: Longitude of the rotation axis in degrees-East
  * `Lat::Float64`: Latitude of the rotation axis in degrees-North
  * `Angle::Float64`: Angle of rotation in degrees
  * `Time::Union{Float64, Nothing}`: Age of rotation in million years
  * `Covariance::Covariance`: [`Covariance`](@ref) in radians²

## Examples:

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
