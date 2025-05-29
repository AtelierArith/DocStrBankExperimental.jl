```
TropicalAndOr <: Number
```

TropicalAndOrは半環代数であり、次のように説明できます。

  * TropicalAndOr, ([T, F], or, and, false, true)。

これは次のようにマッピングします。

  * `+` を通常の代数の `or` に、
  * `*` を通常の代数の `and` に、
  * `1` を通常の代数の `true` に、
  * `0` を通常の代数の `false` に。

## 例

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
