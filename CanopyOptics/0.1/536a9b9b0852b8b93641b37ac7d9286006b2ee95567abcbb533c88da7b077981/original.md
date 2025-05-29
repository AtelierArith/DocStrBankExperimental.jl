dielectric(mod::LiquidPureWater, T::FT,f::FT)

Computes the complex dieletric of liquid pure walter (Ulaby & Long book)

# Arguments

  * `mod` an [`LiquidSaltWater`](@ref) type struct
  * `T`  Temperature in `[⁰K]`
  * `f`  Frequency in `[GHz]`

# Examples

```julia-repl
julia> w = CanopyOptics.LiquidPureWater()     # Create struct for salty seawater
julia> CanopyOptics.dielectric(w,283.0,10.0)
53.45306674215052 + 38.068642430090044im
```
