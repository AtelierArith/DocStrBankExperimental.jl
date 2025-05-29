```
TropicalAndOr <: Number
```

TropicalAndOr is a semiring algebra, can be described by

  * TropicalAndOr, ([T, F], or, and, false, true).

It maps

  * `+` to `or` in regular algebra,
  * `*` to `and` in regular algebra,
  * `1` to `true` in regular algebra,
  * `0` to `false` in regular algebra.

## Example

```jldoctest; setup=:(using TropicalNumbers)
julia> TropicalAndOr(true) + TropicalAndOr(false)
trueₜ

julia> TropicalAndOr(true) * TropicalAndOr(false)
falseₜ

julia> one(TropicalAndOr)
trueₜ

julia> zero(TropicalAndOr)
falseₜ
```
