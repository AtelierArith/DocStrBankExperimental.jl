```
productview(f, a, b)
```

Return a view of a Cartesian product of `a` and `b` where the output elements are `f` evaluated those of `a` and `b`. See also `product` and `ProductArray`

# Example

```julia
julia> productview(+, [1,2], [1,2,3])
2×3 ProductArray{Int64,2,typeof(+),Array{Int64,1},Array{Int64,1}}:
 2  3  4
 3  4  5
```
