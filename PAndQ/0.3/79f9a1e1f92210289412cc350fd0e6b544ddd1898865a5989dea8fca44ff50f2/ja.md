```
operators(p)
```

`p` に含まれる各 [operator](@ref operators_operators) のイテレータを返します。

# 例

```jldoctest
julia> @atomize collect(operators(¬p))
1-element Vector{PAndQ.Interface.Operator{:not}}:
 ¬

julia> @atomize collect(operators(¬p ∧ q))
3-element Vector{PAndQ.Interface.Operator}:
 ∧
 ¬
 𝒾
```
