```
center_set!(arr_large, arr_small)
```

Puts the `arr_small` central into `arr_large`. The convention, where the center is, is the same as the definition as for FFT based centered. Function works both for even and uneven arrays.

# Examples

```jldoctest
julia> DeconvOptim.center_set!([1, 1, 1, 1, 1, 1], [5, 5, 5])
6-element Array{Int64,1}:
 1
 1
 5
 5
 5
 1
```
