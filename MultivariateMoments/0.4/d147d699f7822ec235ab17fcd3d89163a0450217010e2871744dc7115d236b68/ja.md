```
struct LeadingRelativeRankTol{T} <: RankCheck
    tol::T
end
```

ランクは、`tol * maximum(σ)` よりも厳密に大きい特異値の数です。ここで、`maximum(σ)` は最大の特異値です。

## 例

行列がスケーリングが無関係な均質な問題から得られる場合、以下に示すように `LeadingRelativeRankTol` は [`AbsoluteRankTol`](@ref) よりも好ましいかもしれません。

```jldoctest
julia> rank_from_singular_values(1e6 * [1, 1e-1, 5e-2, 1e-5, 5e-6], AbsoluteRankTol(1e-4))
5

julia> rank_from_singular_values(1e6 * [1, 1e-1, 5e-2, 1e-5, 5e-6], LeadingRelativeRankTol(1e-4))
3
```
