```
TropicalMaxPlus{T} = Tropical{T} <: AbstractSemiring
```

TropicalMaxPlusは半環代数であり、次のように説明できます。

  * Tropical (TropicalMaxPlus), (ℝ, max, +, -Inf, 0)。

これは次のようにマッピングします。

  * `+` を通常の代数の `max` に、
  * `*` を通常の代数の `+` に、
  * `1` を通常の代数の `0` に、
  * `0` を通常の代数の `-Inf` に（整数コンテンツタイプの場合、これは小さな整数として選択されます）。

## 例

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
