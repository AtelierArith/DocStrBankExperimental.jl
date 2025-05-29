```
TropicalMinPlus{T} <: AbstractSemiring
```

TropicalMinPlusは半環代数であり、次のように説明できます。

  * TropicalMinPlus, (ℝ, min, +, Inf, 0)。

それは次のようにマッピングします。

  * `+` を通常の代数の `min` に、
  * `*` を通常の代数の `+` に、
  * `1` を通常の代数の `0` に、
  * `0` を通常の代数の `Inf` に（整数コンテンツタイプの場合、これは大きな整数として選択されます）。

## 例

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
