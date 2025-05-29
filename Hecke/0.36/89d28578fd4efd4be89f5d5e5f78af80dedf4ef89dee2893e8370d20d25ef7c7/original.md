```
direct_sum(x::Vararg{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}
direct_sum(x::Vector{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}
```

Given a collection of quadratic or hermitian spaces $V_1, \ldots, V_n$, return their direct sum $V := V_1 \oplus \ldots \oplus V_n$, together with the injections $V_i \to V$.

For objects of type `AbstractSpace`, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain `V` as a direct product with the projections $V \to V_i$, one should call `direct_product(x)`. If one wants to obtain `V` as a biproduct with the injections $V_i \to V$ and the projections $V \to V_i$, one should call `biproduct(x)`.
