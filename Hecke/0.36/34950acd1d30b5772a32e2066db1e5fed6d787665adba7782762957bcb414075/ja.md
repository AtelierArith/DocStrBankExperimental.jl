```
abelian_group(::Type{T} = FinGenAbGroup, M::AbstractVector{<:IntegerUnion}) -> FinGenAbGroup
abelian_group(::Type{T} = FinGenAbGroup, M::IntegerUnion...) -> FinGenAbGroup
```

循環群 $\mathbf{Z}/m_i$ の直積を作成します。ここで、$m_i$ は `M` の $i$ 番目のエントリです。
