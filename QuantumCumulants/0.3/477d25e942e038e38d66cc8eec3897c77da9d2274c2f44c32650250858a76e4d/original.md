```
get_order(arg)
```

Compute the order of a given argument. This is the order used to decide whether something should be expanded using a [`cumulant_expansion`](@ref) method.

# Examples

```
julia> get_order(a)
1

julia> get_order(a*b)
2

julia> get_order(1)
0
```
