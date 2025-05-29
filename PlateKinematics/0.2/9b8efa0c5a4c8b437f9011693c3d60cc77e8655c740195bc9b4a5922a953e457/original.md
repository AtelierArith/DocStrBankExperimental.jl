```julia
struct EulerVectorCart
```

Euler vector in Cartesian coordinates, expressed in degrees/Myr.

## Fields

  * `X::Float64`: X-coordinate in degrees/Myr
  * `Y::Float64`: Y-coordinate in degrees/Myr
  * `Z::Float64`: Z-coordinate in degrees/Myr
  * `TimeRange::Union{Matrix, Nothing}`: Initial to final age of rotation
  * `Covariance::Covariance`: [`Covariance`](@ref) in radians²/Myr²

## Examples:

Same outer Constructor Methods as [`EulerVectorSph`](@ref).
