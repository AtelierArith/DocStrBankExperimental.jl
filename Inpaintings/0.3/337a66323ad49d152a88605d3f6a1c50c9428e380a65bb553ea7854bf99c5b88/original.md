```
inpaint(A)
```

Inpaints `NaN` values if the elements of `A` are all float (i.e., `eltype(A) <: AbstractFloat`).

# Example

```jldoctest
julia> A = float((1:3)*(1:4)') ; A[1:2, 1:2] .= NaN ; A
3×4 Array{Float64,2}:
 NaN    NaN    3.0   4.0
 NaN    NaN    6.0   8.0
   3.0    6.0  9.0  12.0

julia> inpaint(A)
3×4 Array{Float64,2}:
 1.0  2.0  3.0   4.0
 2.0  4.0  6.0   8.0
 3.0  6.0  9.0  12.0
```
