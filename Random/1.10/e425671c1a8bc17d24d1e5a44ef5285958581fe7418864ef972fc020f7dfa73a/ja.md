```
shuffle([rng=default_rng(),] v::AbstractArray)
```

`v`のランダムに順序を入れ替えたコピーを返します。オプションの`rng`引数は乱数生成器を指定します（[Random Numbers](@ref）を参照）。`v`をインプレースで順序を入れ替えるには、[`shuffle!`](@ref)を参照してください。ランダムに順序を入れ替えたインデックスを取得するには、[`randperm`](@ref)を参照してください。

# 例

```jldoctest
julia> rng = MersenneTwister(1234);

julia> shuffle(rng, Vector(1:10))
10-element Vector{Int64}:
  6
  1
 10
  2
  3
  9
  5
  7
  4
  8
```
