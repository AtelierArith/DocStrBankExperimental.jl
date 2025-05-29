```
direct_sum(x::Vararg{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}
direct_sum(x::Vector{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}
```

Given a collection of torsion quadratic modules $T_1, \ldots, T_n$, return their direct sum $T := T_1\oplus \ldots \oplus T_n$, together with the injections $T_i \to T$.

For objects of type `TorQuadModule`, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain `T` as a direct product with the projections $T \to T_i$, one should call `direct_product(x)`. If one wants to obtain `T` as a biproduct with the injections $T_i \to T$ and the projections $T \to T_i$, one should call `biproduct(x)`.
