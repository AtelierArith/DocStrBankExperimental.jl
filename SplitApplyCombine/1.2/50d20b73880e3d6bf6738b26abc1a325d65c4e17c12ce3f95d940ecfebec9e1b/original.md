```
product(f, a, b)
```

Takes the Cartesian outer product of two containers and evaluates `f` on all pairings of elements. 

For example, if `a` and `b` are vectors, this returns a matrix `out` such that `out[i,j] = f(a[i], b[j])` for `i in keys(a)` and `j in keys(b)`. See also `productview`.

# Example

```julia
julia> product(+, [1,2], [1,2,3])
2×3 Array{Int64,2}:
 2  3  4
 3  4  5
```
