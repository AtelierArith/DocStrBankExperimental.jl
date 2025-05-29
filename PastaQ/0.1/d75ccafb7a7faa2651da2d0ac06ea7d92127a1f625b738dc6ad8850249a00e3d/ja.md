```
randomlayer(
  gatename::AbstractString,
  support::Union{Int, Vector{<:Tuple}, AbstractRange};
  rng = Random.GLOBAL_RNG,
  kwargs...
)
```

1つまたは2つの量子ビットゲートのセットから構成されるランダムレイヤーを生成します。 `support::Int = n` の場合、$n$ 個の単一量子ビットゲート `gatename` を生成します。 `support::Vector=bonds` の場合、`support` に含まれる結合に対して2量子ビットゲートのセットを生成します。

```julia
randomlayer("Ry", 3)
# 3-element Vector{Any}:
#  ("Ry", 1, (θ = 0.5029516521736083,))
#  ("Ry", 2, (θ = 2.5324545964433693,))
#  ("Ry", 3, (θ = 2.0510824561219523,))
```
