```
inpaint(f, A)
```

Inpaints values of `A` for which `f(A) == true`.

# Examples

```jldoctest
julia> A = float((1:3)*(1:4)') ; A[1:2, 1:2] .= 999 ; A
3×4 Array{Float64,2}:
 999.0  999.0  3.0   4.0
 999.0  999.0  6.0   8.0
   3.0    6.0  9.0  12.0

julia> inpaint(x -> x == 999, A)
3×4 Array{Float64,2}:
 1.0  2.0  3.0   4.0
 2.0  4.0  6.0   8.0
 3.0  6.0  9.0  12.0
```

```jldoctest
julia> A = float((1:3)*(1:4)') ; A[1:2, [1, end]] .= NaN ; A
3×4 Array{Float64,2}:
 NaN    2.0  3.0  NaN
 NaN    4.0  6.0  NaN
   3.0  6.0  9.0   12.0

julia> inpaint(isnan, A)
3×4 Array{Float64,2}:
 1.0  2.0  3.0   4.0
 2.0  4.0  6.0   8.0
 3.0  6.0  9.0  12.0
```

```
inpaint(f, A; method=1, cycledims=[])
```

With optional arguments, you can chose the inpainting method and if dimensions are cyclic.

```jldoctest
julia> A = float((1:3)*(1:4)') ; A[1:2, [1, end]] .= NaN ; A
3×4 Array{Float64,2}:
 NaN    2.0  3.0  NaN
 NaN    4.0  6.0  NaN
   3.0  6.0  9.0   12.0

julia> inpaint(A, cycledims=[2])
3×4 Array{Float64,2}:
 2.16475  2.0  3.0   2.83525
 3.76245  4.0  6.0   6.23755
 3.0      6.0  9.0  12.0
```
