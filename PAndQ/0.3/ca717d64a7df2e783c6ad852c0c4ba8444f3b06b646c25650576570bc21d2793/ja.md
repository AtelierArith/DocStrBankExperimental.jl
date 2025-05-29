```
is_tautology(p)
```

与えられた命題が [`tautology`](@ref) に論理的に等しいかどうかを示す `Bool`ean を返します。

# 例

```jldoctest
julia> is_tautology(⊤)
true

julia> @atomize is_tautology(p)
false

julia> @atomize is_tautology(¬(p ∧ ¬p))
true
```
