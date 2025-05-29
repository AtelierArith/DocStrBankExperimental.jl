```julia
struct EulerVectorSph
```

Euler vector in spherical coordinates with the following parameters:

## Fields

  * `Lon::Float64`: Longitude of the Euler pole in degrees-East
  * `Lat::Float64`: Latitude of the Euler pole in degrees-North
  * `AngVelocity::Float64`: Angular velocity in degrees/Myr
  * `TimeRange::Union{Matrix, Nothing}`: Initial to final age of rotation
  * `Covariance::Covariance`: [`Covariance`](@ref) in radians²/Myr²

## Examples:

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
