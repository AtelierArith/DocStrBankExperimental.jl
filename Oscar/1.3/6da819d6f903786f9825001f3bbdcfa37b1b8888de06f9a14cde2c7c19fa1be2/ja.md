```
is_even(Lf::ZZLatWithIsom) -> Bool
```

与えられた同型 $(L, f)$ を持つ格子に対して、基礎となる格子 $L$ が偶数であるかどうかを返します。

See [`iseven(::ZZLat)`](@ref).

# 例

```jldoctest
julia> L = root_lattice(:A, 5);

julia> Lf = integer_lattice_with_isometry(L);

julia> is_even(Lf)
true
```
