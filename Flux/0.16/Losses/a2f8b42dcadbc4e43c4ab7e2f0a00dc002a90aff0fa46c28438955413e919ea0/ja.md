```
huber_loss(ŷ, y; delta = 1, agg = mean)
```

予測 `ŷ` と真の値 `y` に基づいて [ハーバーロス](https://en.wikipedia.org/wiki/Huber_loss) の平均を返します。

```
             | 0.5 * |ŷ - y|^2,            もし |ŷ - y| <= δ の場合
ハーバーロス = |
             |  δ * (|ŷ - y| - 0.5 * δ), それ以外の場合
```

# 例

```jldoctest
julia> ŷ = [1.1, 2.1, 3.1];

julia> Flux.huber_loss(ŷ, 1:3)  # デフォルト δ = 1 > |ŷ - y|
0.005000000000000009

julia> Flux.huber_loss(ŷ, 1:3, delta=0.05)  # |ŷ - y| > δ の場合、動作が変わる
0.003750000000000005
```
