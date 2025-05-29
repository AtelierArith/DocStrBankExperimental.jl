```
is_hermitian(t::Dict) -> Bool
```

与えられた型 $t$ の同型を持つ格子が、$t$ がエルミートであるかどうか、すなわち同型を持つエルミート格子の型を定義しているかどうかを返します。

[`is_of_hermitian_type(::ZZLatWithIsom)`](@ref) と [`type(::ZZLatWithIsom)`](@ref) を参照してください。

# 例

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
