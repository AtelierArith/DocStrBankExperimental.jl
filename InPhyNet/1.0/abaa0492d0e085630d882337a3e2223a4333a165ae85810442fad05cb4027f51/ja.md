```
internodecount(N::HybridNetwork; namelist::Union{Nothing,<:AbstractVector{String}}=nothing)
```

ネットワーク `N` 内のすべてのタクサのペア間の内部ノード数を計算します。警告: `N` を根なしとして扱います。
