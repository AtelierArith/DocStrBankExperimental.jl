```
<|(f, args)
```

Applies a function to the succeeding argument or tuple of arguments. Acts as the reverse of [`|>`](@ref), and is especially useful when combined with partial functions for an alternative, low-parenthese function chaining syntax

# Examples

```@jldoctest
julia> using PartialFunctions

julia> isdigit <| '1'
true

julia> (+) <| (2, 3)...
5

julia> map $ Int <| [1.0, 2.0, 3.0]
3-element Vector{Int64}:
 1
 2
 3
```
