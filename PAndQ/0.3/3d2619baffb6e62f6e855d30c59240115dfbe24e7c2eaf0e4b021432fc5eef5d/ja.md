```
is_falsifiable(p)
```

`p`が[falsifiable](https://en.wikipedia.org/wiki/Falsifiability)（[`tautology`](@ref)と論理的に同値でない）であるかどうかを示す`Bool`eanを返します。

# 例

```jldoctest
julia> is_falsifiable(⊥)
true

julia> @atomize is_falsifiable(p ∨ ¬p)
false

julia> @atomize is_falsifiable(p)
true

julia> @atomize is_falsifiable(p ∧ q)
true
```
