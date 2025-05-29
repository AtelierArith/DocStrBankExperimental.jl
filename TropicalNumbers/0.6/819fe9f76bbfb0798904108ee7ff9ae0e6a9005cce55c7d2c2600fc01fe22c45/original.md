```
TropicalMaxMul{T} <: AbstractSemiring
```

TropicalMaxMul is a semiring algebra, can be described by

  * TropicalMaxMul, (ℝ⁺, max, ⋅, 0, 1).

It maps

  * `+` to `max` in regular algebra,
  * `*` to `*` in regular algebra,
  * `1` to `1` in regular algebra,
  * `0` to `0` in regular algebra.

## Example

```jldoctest; setup=:(using TropicalNumbers)
julia> TropicalMaxMul(1.0) + TropicalMaxMul(3.0)
3.0ₓ

julia> TropicalMaxMul(1.0) * TropicalMaxMul(3.0)
3.0ₓ

julia> one(TropicalMaxMulF64)
1.0ₓ

julia> zero(TropicalMaxMulF64)
0.0ₓ
```
