```
is_zero(R::NCRing)
```

Test whether the ring $R$ is trivial. However, the recommended method for doing this is [`is_trivial`](@ref).

```jldoctest
julia> R, (x,) = polynomial_ring(QQ, [:x]);

julia> S=quo(R,1)[1]
Residue ring of R modulo 1

julia> is_trivial(S)
true

julia> is_zero(S)
true
```
