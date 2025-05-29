```
TropicalMaxPlus{T} = Tropical{T} <: AbstractSemiring
```

TropicalMaxPlus is a semiring algebra, can be described by

  * Tropical (TropicalMaxPlus), (ℝ, max, +, -Inf, 0).

It maps

  * `+` to `max` in regular algebra,
  * `*` to `+` in regular algebra,
  * `1` to `0` in regular algebra,
  * `0` to `-Inf` in regular algebra (for integer content types, this is chosen as a small integer).

## Example

```jldoctest; setup=:(using TropicalNumbers)
julia> TropicalMaxPlus(1.0) + TropicalMaxPlus(3.0)
3.0ₜ

julia> TropicalMaxPlus(1.0) * TropicalMaxPlus(3.0)
4.0ₜ

julia> one(TropicalMaxPlusF64)
0.0ₜ

julia> zero(TropicalMaxPlusF64)
-Infₜ
```
