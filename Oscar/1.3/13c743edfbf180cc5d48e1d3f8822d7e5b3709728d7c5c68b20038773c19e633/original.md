```
is_hermitian(t::Dict) -> Bool
```

Given a type $t$ of lattices with isometry, return whether $t$ is hermitian, i.e. whether it defines the type of a hermitian lattice with isometry.

See [`is_of_hermitian_type(::ZZLatWithIsom)`](@ref) and [`type(::ZZLatWithIsom)`](@ref).

# Examples

```jldoctest
julia> L = root_lattice(:A, 5);

julia> f = matrix(QQ, 5, 5, [1  1  1  1  1;
                             0 -1 -1 -1 -1;
                             0  1  0  0  0;
                             0  0  1  0  0;
                             0  0  0  1  0]);

julia> Lf = integer_lattice_with_isometry(L, f);

julia> M = coinvariant_lattice(Lf);

julia> is_hermitian(type(Lf))
false

julia> is_hermitian(type(M))
true
```
