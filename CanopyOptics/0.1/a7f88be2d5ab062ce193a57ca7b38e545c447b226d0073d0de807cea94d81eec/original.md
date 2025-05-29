dielectric(mod::SoilMW, T::FT,f::FT)

Computes the complex dieletric of soil (Ulaby & Long book)

# Arguments

  * `mod` an [`SoilMW`](@ref) type struct (includes sand*frac, clay*frac, water_frac, ρ)
  * `T`  Temperature in `[⁰K]`
  * `f`  Frequency in `[GHz]`

# Examples

```julia-repl
julia> w = SoilMW(sand_frac=0.2,clay_frac=0.2, water_frac = 0.3, ρ=1.7 )     # Create struct for salty seawater
julia> dielectric(w,283.0,10.0)
53.45306674215052 + 38.068642430090044im
```
