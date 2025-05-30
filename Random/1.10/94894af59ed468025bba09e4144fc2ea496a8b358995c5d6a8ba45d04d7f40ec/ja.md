```
shuffle!([rng=default_rng(),] v::AbstractArray)
```

[`shuffle`](@ref) のインプレースバージョン：`v` をインプレースでランダムに順序を入れ替え、オプションで乱数生成器 `rng` を指定します。

# 例

```jldoctest
julia> rng = MersenneTwister(1234);

julia> shuffle!(rng, Vector(1:16))
16-element Vector{Int64}:
  2
 15
  5
 14
  1
  9
 10
  6
 11
  3
 16
  7
  4
 12
  8
 13
```
