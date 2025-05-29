```
nshuffle!([rng=GLOBAL_RNG,], c, n::Integer, s::AbstractShuffle=RandomShuffle())
```

コレクション `c` をアルゴリズム `s` を使用して `n` 回インプレースでシャッフルします。ランダムシャッフルアルゴリズムには、ランダム数生成器 `rng` を指定できます。

# 例

```jldoctest
julia> mt = MersenneTwister(1234);

julia> a = collect(1:7);

julia> nshuffle!(mt, a, 3, GilbertShannonReeds()); a
7-element Array{Int64,1}:
 5
 6
 1
 7
 2
 3
 4
```
