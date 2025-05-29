```
is_even(Lf::ZZLatWithIsom) -> Bool
```

Given a lattice with isometry $(L, f)$, return whether the underlying lattice $L$ is even.

See [`iseven(::ZZLat)`](@ref).

# Examples

```jldoctest
julia> L = root_lattice(:A, 5);

julia> Lf = integer_lattice_with_isometry(L);

julia> is_even(Lf)
true
```
