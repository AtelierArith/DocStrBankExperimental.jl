```
cpx([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit)
```

See `rr2` for a description of all options.

Returns an IndexFunArray where each positon corresponds to a complex value according to its position. The parameters `offset` and `scale` can be used accordingly (see `rr2`). Note that `T` is enforced element-wise for the return tuple elements.

```jldoctest
julia> cpx(Int, (3,3), offset=CtrCorner)
3×3 Matrix{Complex{Int64}}:
 0+0im  0+1im  0+2im
 1+0im  1+1im  1+2im
 2+0im  2+1im  2+2im

julia> cpx(Int, (3,3), offset=(0,0))
3×3 Matrix{Complex{Int64}}:
 1+1im  1+2im  1+3im
 2+1im  2+2im  2+3im
 3+1im  3+2im  3+3im

julia> cpx((3,3), offset=(0,0))
3×3 Matrix{ComplexF64}:
 1.0+1.0im  1.0+2.0im  1.0+3.0im
 2.0+1.0im  2.0+2.0im  2.0+3.0im
 3.0+1.0im  3.0+2.0im  3.0+3.0im
```
