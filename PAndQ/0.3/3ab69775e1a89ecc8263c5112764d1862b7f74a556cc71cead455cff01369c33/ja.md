```
is_equisatisfiable(p, q)
```

述語 [`is_satisfiable`](@ref) が両方の命題に対して合同であるかどうかを示す `Bool`ean を返します。

# 例

```jldoctest
julia> is_equisatisfiable(⊤, ⊥)
false

julia> @atomize is_equisatisfiable(p, q)
true
```
