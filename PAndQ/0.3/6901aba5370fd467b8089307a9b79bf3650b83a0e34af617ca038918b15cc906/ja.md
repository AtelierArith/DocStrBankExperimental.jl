```
is_contingency(p)
```

`p`が[偶然](https://en.wikipedia.org/wiki/Contingency_(philosophy))（[真理値](@ref nullary_operators)と論理的に同値でない）であるかどうかを示す`Bool`eanを返します。

# 例

```jldoctest
julia> is_contingency(⊤)
false

julia> @atomize is_contingency(p ∧ ¬p)
false

julia> @atomize is_contingency(p)
true

julia> @atomize is_contingency(p ∧ q)
true
```
