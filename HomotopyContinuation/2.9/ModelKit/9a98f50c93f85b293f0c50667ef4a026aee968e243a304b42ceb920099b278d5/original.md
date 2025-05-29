```
Variable(name::Union{String,Symbol}, indices...) <: Number
```

A data structure representing a variable.

```julia-repl
julia> Variable(:a)
a

julia> Variable(:x, 1)
x₁

julia> Variable(:x, 10, 5)
x₁₀₋₅
```

### Equality and ordering

Variables are identified by their `name` and `indices`. That is, two variables are equal if and only if they have the same `name` and `indices`.

```julia-repl
julia> Variable(:a) == Variable(:a)
true

julia> Variable(:a, 1) == Variable(:a, 2)
false
```

Similarly, variables are first ordered lexicographically by their name and then by their indices.

```julia-repl
julia> Variable(:a, 1) < Variable(:a, 2)
true

julia> Variable(:a, 1) < Variable(:b, 1)
true

julia> a = [Variable(:a, i, j) for i in 1:2, j in 1:2]
2×2 Array{Variable,2}:
 a₁₋₁  a₁₋₂
 a₂₋₁  a₂₋₂

julia> sort(vec(a))
4-element Array{Variable,1}:
 a₁₋₁
 a₂₋₁
 a₁₋₂
 a₂₋₂
```
