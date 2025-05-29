```
biproduct(x::Vararg{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}, Vector{TorQuadModuleMap}
biproduct(x::Vector{TorQuadModule}) -> TorQuadModule, Vector{TorQuadModuleMap}, Vector{TorQuadModuleMap}
```

Given a collection of torsion quadratic modules $T_1, \ldots, T_n$, return their biproduct $T := T_1\oplus \ldots \oplus T_n$, together with the injections $T_i \to T$ and the projections $T \to T_i$.

For objects of type `TorQuadModule`, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain `T` as a direct sum with the inctions $T_i \to T$, one should call `direct_sum(x)`. If one wants to obtain `T` as a direct product with the projections $T \to T_i$, one should call `direct_product(x)`.
