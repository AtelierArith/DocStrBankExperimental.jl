dielectric(mod::LiquidSaltWater, T::FT,f::FT)

Computes the complex dieletric of liquid salty walter (Ulaby & Long book)

# Arguments

  * `mod` an [`LiquidSaltWater`](@ref) type struct, provide Salinity in PSU
  * `T`  Temperature in `[⁰K]`
  * `f`  Frequency in `[GHz]`
  * `S`  Salinity in `[PSU]` comes from the `mod` [`LiquidSaltWater`](@ref) struct

# Examples

```julia-repl
julia> w = CanopyOptics.LiquidSaltWater(S=10.0)     # Create struct for salty seawater
julia> CanopyOptics.dielectric(w,283.0,10.0)
51.79254073931596 + 38.32304044382495im
```
