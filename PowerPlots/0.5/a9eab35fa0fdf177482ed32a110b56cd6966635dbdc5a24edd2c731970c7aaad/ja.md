```
`kamada_kawai(
    G::PowerModelsGraph,
    dist::Union{Nothing,AbstractMatrix{<:Real}}=nothing,
    pos::Union{Nothing,AbstractMatrix{<:Real}}=nothing,
    weight="weight",
    scale=1,
    center=nothing,
    dim=2)
`
ノードの位置をKamada Kawaiレイアウトアルゴリズムを使用して計算します
```
