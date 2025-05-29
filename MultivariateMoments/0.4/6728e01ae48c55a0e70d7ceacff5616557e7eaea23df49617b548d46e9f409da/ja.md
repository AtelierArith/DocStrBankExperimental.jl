```
struct AbsoluteRankTol{T} <: RankCheck
    tol::T
end
```

ランクは、`tol` よりも厳密に大きい特異値の数です。

## 例

```jldoctest
julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-5, 5e-6], AbsoluteRankTol(1e-4))
3
```
