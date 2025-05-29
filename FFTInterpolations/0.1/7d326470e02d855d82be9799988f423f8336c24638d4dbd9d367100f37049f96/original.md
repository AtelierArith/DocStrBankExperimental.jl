```
sinc_interpolate_sum(arr, new_length)
```

Calculates the `sinc` interpolation of an 1D `arr` on a new array size `new_size`.  This method is slow, because of an explicit sum evalulation and not a FFT based evaluation.

# Examples

```jldoctest
julia> sinc_interpolate_sum([1.0, 2.0, 3.0, 4.0], 8)
8-element Array{Float64,1}:
 1.0
 1.7825353626292277
 2.0
 2.1220659078919377
 3.0
 4.1592491794681985
 4.0
 2.0735615442829793
```
