```
krull_dim(R::Ring)
```

Return the Krull dimension of the ring $R$. The method is currently only supported for certain commutative Noetherian Rings.

# Examples

```jldoctest
julia> R, x = polynomial_ring(ZZ, [:x]);

julia> krull_dim(R)
2
```
