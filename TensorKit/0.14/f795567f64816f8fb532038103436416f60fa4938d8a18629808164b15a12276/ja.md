```
domain(t::AbstractTensorMap{T,S,N₁,N₂}) -> ProductSpace{S,N₂}
domain(t::AbstractTensorMap{T,S,N₁,N₂}, i::Int) -> S
```

テンソルのドメイン、すなわち入力空間の積空間を返します。`i`が指定されている場合は、`i`-番目の入力空間を返します。実装は`domain(t)`を提供する必要があります。

[`codomain`](@ref)および[`space`](@ref)も参照してください。
