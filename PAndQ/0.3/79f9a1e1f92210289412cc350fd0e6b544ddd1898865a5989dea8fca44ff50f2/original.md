```
operators(p)
```

Return an iterator of each [operator](@ref operators_operators) contained in `p`.

# Examples

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
