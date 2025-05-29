```
nshuffle([rng=GLOBAL_RNG,], c, n::Integer, s::AbstractShuffle=RandomShuffle())
```

コレクション `c` をシャッフルアルゴリズム `s` を使用して `n` 回シャッフルします。ランダムシャッフルアルゴリズムには、ランダム数生成器 `rng` を指定できます。`c` をインプレースでシャッフルするには [`nshuffle!`](@ref) を参照してください。

# 例

```jldoctest
julia> nshuffle(collect(1:8), 3, Faro{:in}())
8-element Array{Int64,1}:
 8
 7
 6
 5
 4
 3
 2
 1
```
