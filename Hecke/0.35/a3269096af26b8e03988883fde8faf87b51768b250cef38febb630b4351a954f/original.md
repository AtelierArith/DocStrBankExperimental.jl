```
direct_product(x::Vararg{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}
direct_product(x::Vector{T}) where T <: AbstractSpace -> T, Vector{AbstractSpaceMor}
```

Given a collection of quadratic or hermitian spaces $V_1, \ldots, V_n$, return their direct product $V := V_1 \times \ldots \times V_n$, together with the projections $V \to V_i$.

For objects of type `AbstractSpace`, finite direct sums and finite direct products agree and they are therefore called biproducts. If one wants to obtain `V` as a direct sum with the injections $V_i \to V$, one should call `direct_sum(x)`. If one wants to obtain `V` as a biproduct with the injections $V_i \to V$ and the projections $V \to V_i$, one should call `biproduct(x)`.
