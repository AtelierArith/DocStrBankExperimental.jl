```
shuffle!([rng=GLOBAL_RNG,], c, s::AbstractShuffle=RandomShuffle())
```

コレクション `c` をシャッフルアルゴリズム `s` を使用してインプレースでシャッフルします。ランダムシャッフルアルゴリズムには、ランダム数生成器 `rng` を指定できます。

# 例

```jldoctest
julia> mt = MersenneTwister(1234);

julia> a = collect(1:6);

julia> shuffle!(mt, a); a
6-element Array{Int64,1}:
 2
 1
 3
 6
 4
 5

julia> shuffle!(a, Faro{:out}()); a
6-element Array{Int64,1}:
 2
 6
 1
 4
 3
 5
```
