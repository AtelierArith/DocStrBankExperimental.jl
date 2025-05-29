```
base_ring_type(a)
```

Return the type of the base ring of the given element, element type, parent or parent type $a$.

# Examples

```jldoctest
julia> R, x = polynomial_ring(ZZ, :x)
(Univariate polynomial ring in x over integers, x)

julia> base_ring_type(R) == typeof(base_ring(R))
true

julia> base_ring_type(zero(R)) == typeof(base_ring(zero(R)))
true

julia> base_ring_type(typeof(R)) == typeof(base_ring(R))
true

julia> base_ring_type(typeof(zero(R))) == typeof(base_ring(zero(R)))
true
```
