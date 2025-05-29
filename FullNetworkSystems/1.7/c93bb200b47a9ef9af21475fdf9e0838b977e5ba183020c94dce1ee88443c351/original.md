```julia
struct Zone
```

Type defining a market zone.  The `Zone` is identified by a number.  The other fields contain the service requirements for the zone.  Requirements are given in `pu` assuming a base power of 100MW.

Fields:

  * `number::Int64`: Zone number
  * `regulation::Float64`: Zonal regulation requirement (pu)
  * `operating_reserve::Float64`: Zonal operating reserve requirement (regulation + spinning + supplemental) (pu)
  * `good_utility::Float64`: Zonal good utility practice requirement (regulation + spinning) (pu)
