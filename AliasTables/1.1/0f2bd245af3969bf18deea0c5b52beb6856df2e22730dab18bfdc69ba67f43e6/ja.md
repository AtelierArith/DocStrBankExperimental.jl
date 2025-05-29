```
AliasTable{T<:Unsigned=UInt64, I<:Integer=Int}(weights::AbstractVector{<:Real})
```

離散分布からサンプリングするための効率的なデータ構造です。

`T` で表現可能なすべての値を `weights` の `eachindex(weights)` の型 `I` の値にマッピングし、特定のインデックスの `weights` の値に比例してそのインデックスにマッピングされる値の数を決定します。

マッピングには、[`AliasTables.sample(x::T, at::AliasTable{T, I})`](@ref AliasTables.sample) を介して直接アクセスするか、`Random` API を介して間接的にアクセスできます: `rand(at)`, `rand(rng, at)`, `rand(at, dims...)` など。

さらに [`AliasTables.set_weights!`](@ref) も参照してください。

# 例

```jldoctest; filter=[r" [1-3]"]
julia> at = AliasTable([1, 3, 1])
AliasTable([0x3333333333333334, 0x9999999999999999, 0x3333333333333333])

julia> rand(at, 5)
5-element Vector{Int64}:
 2
 3
 2
 2
 3
```
