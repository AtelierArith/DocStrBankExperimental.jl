```
is_truth(p)
```

与えられた命題が論理的に[真理値](@ref nullary_operators)と同等であるかどうかを示す`Bool`eanを返します。

# 例

```jldoctest
julia> is_truth(⊤)
true

julia> @atomize is_truth(p ∧ ¬p)
true

julia> @atomize is_truth(p)
false

julia> @atomize is_truth(p ∧ q)
false
```
