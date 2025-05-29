```
ramp(::Type{T}, dim::Int, dim_size::Int;
    offset=CtrFT, scale=ScaUnit,
    weight=1,
    accumulator=sum) where {T}
```

Generates a dim-dimensional ramp of size `dim_size` to be used for broadcasting through multidimensional expressions. `dim` highest dimension of the oriented array to be generated. This is also the ramp direction. `dim_size` size along this dimension.

For details about offset and scale and dims see rr2.

```jldoctest
julia> ramp(Float32, 1, 7; offset=(2,))
7-element IndexFunArray{Float32, 1, IndexFunArrays.var"#434#435"{Tuple{Int64}, Tuple{Int64}, Int64}}:
 -1
  0
  1
  2
  3
  4
  5
```

ramp(dim::Int, dim_size::Int; offset=CtrFt, scaling=ScaUnit)

This is a wrapper for  `ramp(Float64, dim::Int, dim_size::Int; offset=CtrFt, scaling=ScaUnit)`.
