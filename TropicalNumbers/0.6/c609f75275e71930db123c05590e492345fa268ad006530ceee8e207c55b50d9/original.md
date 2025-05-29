```
TropicalMinPlus{T} <: AbstractSemiring
```

TropicalMinPlus is a semiring algebra, can be described by

  * TropicalMinPlus, (ℝ, min, +, Inf, 0).

It maps

  * `+` to `min` in regular algebra,
  * `*` to `+` in regular algebra,
  * `1` to `0` in regular algebra,
  * `0` to `Inf` in regular algebra (for integer content types, this is chosen as a large integer).

## Example

```jldoctest; setup=:(using TropicalNumbers)
julia> TropicalMinPlus(1.0) + TropicalMinPlus(3.0)
1.0ₛ

julia> TropicalMinPlus(1.0) * TropicalMinPlus(3.0)
4.0ₛ

julia> one(TropicalMinPlusF64)
0.0ₛ

julia> zero(TropicalMinPlusF64)
Infₛ
```
