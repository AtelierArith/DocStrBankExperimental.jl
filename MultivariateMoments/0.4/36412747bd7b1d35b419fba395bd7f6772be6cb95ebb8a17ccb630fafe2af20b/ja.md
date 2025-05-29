```
struct LargestDifferentialRank <: RankCheck
end
```

ランクは、次の特異値との比率が最も大きい特異値までの特異値の数です。

## 例

[`DifferentialRankTol`](@ref)で使用する許容誤差を決定するのは時々難しいです。たとえば、`1e-2`を選択すると、以下の例では`1e-2`、`5e-2`、`1e-3`はランクの一部ではないと見なされますが、`LargestDifferentialRank`は後に最大のギャップがあるため、それらを含めます。

```jldoctest
julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 1e-6, 5e-7], DifferentialRankTol(1e-2))
1

julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 1e-6, 5e-7], LargestDifferentialRank())
4
```
