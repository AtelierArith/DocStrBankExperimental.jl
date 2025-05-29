```
direct_product(x::Vararg{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}
direct_product(x::Vector{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}
```

Given a collection of torsion quadratic modules $T_1, \ldots, T_n$, return their direct product $T := T_1\times \ldots \times T_n$, together with the projections $T \to T_i$.

For objects of type `TorQuadModule`, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain `T` as a direct sum with the inctions $T_i \to T$, one should call `direct_sum(x)`. If one wants to obtain `T` as a biproduct with the injections $T_i \to T$ and the projections $T \to T_i$, one should call `biproduct(x)`.
