```
absolute_error(a::Vector{<:Number}, b::Vector{<:Number})
```

Compute absolute error between vectors `a` and `b`.

# Examples

```julia-repl
julia> a = [1, 2]; b = [1, 1]; absolute_error(a, b)
1.0
```
