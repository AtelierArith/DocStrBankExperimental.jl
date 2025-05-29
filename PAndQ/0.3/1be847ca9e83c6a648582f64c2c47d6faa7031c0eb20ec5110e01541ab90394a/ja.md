```
is_satisfiable(p)
```

`p`が[satisfiable](https://en.wikipedia.org/wiki/Satisfiability)（[`contradiction`](@ref)と論理的に同値でない）であるかどうかを示す`Bool`eanを返します。

# 例

```jldoctest
julia> is_satisfiable(⊤)
true

julia> @atomize is_satisfiable(p ∧ ¬p)
false

julia> @atomize is_satisfiable(p)
true

julia> @atomize is_satisfiable(p ∧ q)
true
```
