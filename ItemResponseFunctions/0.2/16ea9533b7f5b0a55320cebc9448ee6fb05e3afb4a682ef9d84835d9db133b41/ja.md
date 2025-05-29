```julia
iif!(M, infos, theta, beta)

```

[`iif`](@ref) のインプレースバージョン。`infos` をインプレースで変更することにより、アイテムカテゴリ情報関数の効率的な計算を提供し、中間配列や出力ベクトルの割り当てを回避します。

## 例

```jldoctest
julia> beta = (a = 0.3, b = 0.1, t = (0.2, -0.5));

julia> infos = zeros(length(beta.t) + 1);

julia> iif!(GPCM, infos, 0.0, beta)
3-element Vector{Float64}:
 0.019962114838441732
 0.020570051742573044
 0.0171815514677598

julia> infos
3-element Vector{Float64}:
 0.019962114838441732
 0.020570051742573044
 0.0171815514677598
```
