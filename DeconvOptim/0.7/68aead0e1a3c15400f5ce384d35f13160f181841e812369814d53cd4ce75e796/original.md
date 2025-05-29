```
center_extract(arr, new_size_array)
```

Extracts a center of an array.  `new_size_array` must be list of sizes indicating the output size of each dimension. Centered means that a center frequency stays at the center position. Works for even and uneven. If `length(new_size_array) < length(ndims(arr))` the remaining dimensions are untouched and copied.

# Examples

```jldoctest
julia> DeconvOptim.center_extract([1 2; 3 4], [1]) 
1×2 Array{Int64,2}:
 3  4
julia> DeconvOptim.center_extract([1 2; 3 4], [1, 1])
1×1 Array{Int64,2}:
 4
julia> DeconvOptim.center_extract([1 2 3; 3 4 5; 6 7 8], [2 2])
2×2 Array{Int64,2}:
 1  2
 3  4
```
