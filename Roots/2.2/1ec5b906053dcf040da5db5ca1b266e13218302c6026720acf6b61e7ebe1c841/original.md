```
AllZeros
```

Type to indicate to `solve` that `find_zeros` should be used to solve the given  `ZeroProblem`.

## Example

```
julia> Z = ZeroProblem(cos, (0, 2pi));

julia> solve(Z, AllZeros())
2-element Vector{Float64}:
 1.5707963267948966
 4.71238898038469
```
