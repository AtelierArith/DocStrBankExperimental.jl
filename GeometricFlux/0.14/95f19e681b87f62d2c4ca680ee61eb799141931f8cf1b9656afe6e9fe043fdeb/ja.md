```
DeepSet(ϕ, ρ, aggr=+)
```

ディープセットモデル。

# 引数

  * `ϕ`: 集約前の各入力に対するニューラルネットワーク層。
  * `ρ`: 集約後のニューラルネットワーク層。
  * `aggr`: メッセージ関数の結果に適用される集約関数。`+`、`-`、

`*`、`/`、`max`、`min`、および `mean` が利用可能です。

# 例

```jldoctest
julia> ϕ = Dense(64, 16)
Dense(64 => 16)     # 1_040 パラメータ

julia> ρ = Dense(16, 4)
Dense(16 => 4)      # 68 パラメータ

julia> DeepSet(ϕ, ρ)
DeepSet(Dense(64 => 16), Dense(16 => 4), aggr=+)

julia> DeepSet(ϕ, ρ, aggr=max)
DeepSet(Dense(64 => 16), Dense(16 => 4), aggr=max)
```

静的グラフでのトレーニング層については [`WithGraph`](@ref) を参照してください。
