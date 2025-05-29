```
remove_weight_norms(x)
```

モデル内の[WeightNorm](@ref)パラメータ化を削除します。

### 例

```jldoctest
julia> model = Chain(
           WeightNorm(Conv((3,), 1 => 2), :weight),
           WeightNorm(Conv((3,), 2 => 2), :weight),
       )
Chain(
  WeightNorm(
    Conv((3,), 1 => 2),                 # 8 パラメータ
    3×1×1 Array{Float32,...},           # 3 パラメータ
    :weight,
    3,
  ),
  WeightNorm(
    Conv((3,), 2 => 2),                 # 14 パラメータ
    3×2×1 Array{Float32,...},           # 6 パラメータ
    :weight,
    3,
  ),
)                   # 合計: 6 配列, 31 パラメータ, 588 バイト。

julia> Flux.remove_weight_norms(model)
Chain(
  Conv((3,), 1 => 2),                   # 8 パラメータ
  Conv((3,), 2 => 2),                   # 14 パラメータ
)                   # 合計: 4 配列, 22 パラメータ, 392 バイト。
```
