```
bitrand([rng=default_rng()], [dims...])
```

ランダムなブール値の `BitArray` を生成します。

# 例

```jldoctest
julia> rng = MersenneTwister(1234);

julia> bitrand(rng, 10)
10-element BitVector:
 0
 0
 0
 0
 1
 0
 0
 0
 1
 1
```
