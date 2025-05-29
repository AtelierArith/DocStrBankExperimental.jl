```
embedding(p::InfPlc) -> NumFieldEmb
```

Given a real infinite place, return the unique real embedding defining this place. If the infinite place is not real, an error is thrown.

See also [`embeddings`](@ref).

# Examples

```jldoctest
julia> K, a = quadratic_field(5);

julia> embedding(real_places(K)[1])
Real embedding
  of real quadratic field defined by x^2 - 5
corresponding to root -2.24
```
