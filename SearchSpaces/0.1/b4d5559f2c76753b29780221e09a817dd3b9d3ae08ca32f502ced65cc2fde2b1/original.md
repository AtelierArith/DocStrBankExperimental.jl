```
..(a, b)
```

Define a interval between a and b (inclusive).

# Example

```julia-repl
julia> my_interval = (-π..π)

julia> rand(my_interval, 5)
5-element Vector{Float64}:
 0.5111482297554093
 1.1984728844571544
 1.3279941255812906
 2.3429444282250502
 3.0495310142685526
```

See also [`BoxConstrainedSpace`](@ref)
