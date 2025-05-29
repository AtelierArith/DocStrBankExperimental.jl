```
abelian_group(::Type{T} = FinGenAbGroup, M::AbstractVector{<:IntegerUnion}) -> FinGenAbGroup
abelian_group(::Type{T} = FinGenAbGroup, M::IntegerUnion...) -> FinGenAbGroup
```

Creates the direct product of the cyclic groups $\mathbf{Z}/m_i$, where $m_i$ is the $i$th entry of `M`.
