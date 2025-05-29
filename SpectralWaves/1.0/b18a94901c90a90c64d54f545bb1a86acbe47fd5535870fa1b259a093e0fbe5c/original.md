```
relative_error(a::Vector{<:Number}, b::Vector{<:Number})
```

Compute relative error between vectors `a` and `b`.

# Examples

```julia-repl
julia> a = [2, 2]; b = [1, 1]; relative_error(a, b)
0.5
```
