```
codomain(t::AbstractTensorMap{T,S,N₁,N₂}) -> ProductSpace{S,N₁}
codomain(t::AbstractTensorMap{T,S,N₁,N₂}, i::Int) -> S
```

テンソルのコドメイン、すなわち出力空間の積空間を返します。`i`が指定されている場合は、`i`-番目の出力空間を返します。実装は`codomain(t)`を提供する必要があります。

[`domain`](@ref)および[`space`](@ref)も参照してください。
