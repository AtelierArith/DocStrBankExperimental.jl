```
biproduct(x::Vararg{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
biproduct(x::Vector{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}, Vector{AbstractSpaceMor}
```

Given a collection of quadratic or hermitian spaces $V_1, \ldots, V_n$, return their biproduct $V := V_1 \oplus \ldots \oplus V_n$, together with the injections $V_i \to V$ and the projections $V \to V_i$.

For objects of type `AbstractSpace`, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain `V` as a direct sum with the injections $V_i \to V$, one should call `direct_sum(x)`. If one wants to obtain `V` as a direct product with the projections $V \to V_i$, one should call `direct_product(x)`.
