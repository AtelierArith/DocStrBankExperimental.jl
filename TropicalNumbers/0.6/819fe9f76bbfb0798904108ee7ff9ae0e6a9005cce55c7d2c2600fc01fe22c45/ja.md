```
TropicalMaxMul{T} <: AbstractSemiring
```

TropicalMaxMulは半環代数であり、次のように記述できます。

  * TropicalMaxMul, (ℝ⁺, max, ⋅, 0, 1)。

それは次のようにマッピングします。

  * `+` を通常の代数の `max` に、
  * `*` を通常の代数の `*` に、
  * `1` を通常の代数の `1` に、
  * `0` を通常の代数の `0` に。

## 例

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
