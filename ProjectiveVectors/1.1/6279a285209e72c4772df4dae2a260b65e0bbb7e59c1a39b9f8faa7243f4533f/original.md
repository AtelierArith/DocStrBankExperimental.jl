```
affine_chart(z::PVector)
```

Return the affine chart corresponding to the projective vector. This can be seen as the inverse of [`embed`](@ref).

## Example

```julia-repl
julia> v = embed([2.0, 3, 4, 5, 6, 7], (2, 3, 1))
PVector{Float64, 3}:
 [2.0, 3.0, 1.0] × [4.0, 5.0, 6.0, 1.0] × [7.0, 1.0]

julia> affine_chart(v)
6-element Array{Float64,1}:
 2.0
 3.0
 4.0
 5.0
 6.0
 7.0
```
