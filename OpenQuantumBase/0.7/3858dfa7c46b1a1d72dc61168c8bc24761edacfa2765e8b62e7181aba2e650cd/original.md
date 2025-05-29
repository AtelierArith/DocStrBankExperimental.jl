```julia
find_degenerate(w; digits)

```

Calculate the indices of the degenerate values in list `w`. `w` must be sorted in ascending order.

If the `digits` keyword argument is provided, it rounds the energies to the specified number of digits after the decimal place (or before if negative), in base 10. The default value is 8.

# Examples

```julia-repl
julia> w = [1,1,1,2,3,4,4,5]
julia> find_degenerate(w)
2-element Array{Array{Int64,1},1}:
 [1, 2, 3]
 [6, 7]
```
