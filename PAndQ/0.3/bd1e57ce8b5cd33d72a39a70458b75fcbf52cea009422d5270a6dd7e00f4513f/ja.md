```
is_contradiction(p)
```

与えられた命題が [`contradiction`](@ref) と論理的に同値であるかどうかを示す `Bool`ean を返します。

# 例

```jldoctest
julia> is_contradiction(⊥)
true

julia> @atomize is_contradiction(p)
false

julia> @atomize is_contradiction(p ∧ ¬p)
true
```
