```
RandomShuffle
```

フィールドを持たないタイプで、単一のインスタンス [`randshuffle`](@ref) を持つ完全にランダムなシャッフルを表します。

このアルゴリズムはデフォルトとして設定されています。 [`DEFAULTS`](@ref) を参照してください。

# 例

```jldoctest
julia> mt = MersenneTwister(1234);

julia> shuffle(mt, 1:7, randshuffle)
7-element Array{Int64,1}:
 1
 2
 3
 7
 6
 4
 5

```
