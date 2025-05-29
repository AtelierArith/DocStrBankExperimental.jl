`cycles(a::Perm)` returns the cycles of `a`

# Example

```julia-repl
julia> cycles(Perm(1,2)*Perm(4,5))
2-element Vector{Vector{Int16}}:
 [1, 2]
 [4, 5]
```
