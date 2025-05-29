```
sinc_interpolate(arr, new_size [, normalize])
```

Calculates the `sinc` interpolation of an `arr` on a new array size `new_size`. This method is based on FFTs and therefore implicitly assumes periodic boundaries and a finite frequeny support. `normalize=true` by default multiplies by an appropriate factor so that  the average intensity stays the same.

# Examples

```jldoctest
julia> sinc_interpolate([1.0, 2.0, 3.0, 4.0], 8)
8-element Array{Float64,1}:
 1.0
 1.085786437626905
 2.0
 2.5
 3.0
 3.914213562373095
 4.0
 2.5

julia> sinc_interpolate([1.0  2.0; 3.0 4.0], (4,4))
4×4 Array{Float64,2}:
 1.0  1.5  2.0  1.5
 2.0  2.5  3.0  2.5
 3.0  3.5  4.0  3.5
 2.0  2.5  3.0  2.5
```
