```
is_noetherian(R::Ring)
```

Check if the ring $R$ is Noetherian.

# Examples

```jldoctest
julia> R, x = polynomial_ring(ZZ, [:x]);

julia> is_noetherian(R)
true
```
