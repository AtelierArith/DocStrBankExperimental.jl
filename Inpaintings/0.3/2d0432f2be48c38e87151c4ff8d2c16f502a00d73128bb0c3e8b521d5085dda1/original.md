```
inpaint(A)
```

Inpaints `missing` values if `A` contains some.

Inspired by MATLAB's `inpaint_nans`'s (by John d'Errico: [link](https://www.mathworks.com/matlabcentral/fileexchange/4551-inpaint_nans)).

# Example

```jldoctest
julia> A = convert(Array{Union{Float64, Missing},2}, (1:3)*(1:4)') ; A[1:2, 1:2] .= missing ; A
3×4 Array{Union{Missing, Float64},2}:
  missing   missing  3.0   4.0
  missing   missing  6.0   8.0
 3.0       6.0       9.0  12.0

julia> inpaint(A)
3×4 Array{Union{Missing, Float64},2}:
 1.0  2.0  3.0   4.0
 2.0  4.0  6.0   8.0
 3.0  6.0  9.0  12.0
```
