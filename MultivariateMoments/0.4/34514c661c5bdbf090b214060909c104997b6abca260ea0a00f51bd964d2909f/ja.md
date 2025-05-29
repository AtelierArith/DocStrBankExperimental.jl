```
struct DifferentialRankTol{T} <: RankCheck
    tol::T
end
```

ランクは、特異値が `tol` 倍の前の特異値（含む）よりも小さい特異値の数です（含まない）。

## 例

[`LeadingRelativeRankTol`](@ref) で使用する許容誤差を決定するのは時々難しいです。たとえば、`1e-3` を選択すると、以下の例では `1e-3` はランクの一部とは見なされませんが、`DifferentialRankTol` はそれを含めます。なぜなら、それは前の特異値に近いからです。

```jldoctest
julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-2, 5e-3, 1e-3, 1e-6, 5e-7], LeadingRelativeRankTol(1e-3))
5

julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-2, 5e-3, 1e-3, 1e-6, 5e-7], DifferentialRankTol(1e-2))
6
```
