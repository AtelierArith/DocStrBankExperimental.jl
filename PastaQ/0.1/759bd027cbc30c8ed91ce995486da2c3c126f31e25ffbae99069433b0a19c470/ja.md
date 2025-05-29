```
randomlayer(
  gatenames::Vector{<:AbstractString},
  support::Union{Vector{<:Int}, AbstractRange, Vector{<:Tuple}};
  rng=Random.GLOBAL_RNG,
  weights::Union{Nothing,Vector{Float64}} = ones(length(gatenames)) / length(gatenames),
  kwargs...,
)
```

1つまたは2つの量子ビットゲートで構成されたランダムレイヤーを生成します。ここで、`gatenames`は選択可能なゲートのセットです。デフォルトでは、各単一ゲートはこのセットから一様にサンプリングされます。`weights`が提供されている場合、各ゲートはそれに応じてサンプリングされます。

```julia
randomlayer(["X","Y","Z"], 3)
# 3-element Vector{Any}:
#  ("Y", 1)
#  ("Y", 2)
#  ("X", 3)
```
