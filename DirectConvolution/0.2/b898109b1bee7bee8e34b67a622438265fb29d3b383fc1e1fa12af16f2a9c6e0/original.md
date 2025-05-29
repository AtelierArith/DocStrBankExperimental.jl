```
boundaryExtension(β::AbstractArray{T,1},
                  k::Int,
                  ::Type{BOUNDARY_EXT_TYPE})
```

Computes extended boundary value `β[k]` given boundary extension type `BOUNDARY_EXT_TYPE`

Available `BOUNDARY_EXT_TYPE` are:

  * `ZeroPaddingBE`: zero padding
  * `ConstantBE`: constant boundary extension padding
  * `PeriodicBE`: periodic boundary extension padding
  * `MirrorBE`: mirror symmetry boundary extension padding

The routine is robust in the sens that there is no restriction on `k` value.

```jldoctest
julia> dom = [-5:10;];

julia> hcat(dom,map(x->boundaryExtension([1; 2; 3],x,ZeroPaddingBE),dom))'
2×16 adjoint(::Matrix{Int64}) with eltype Int64:
 -5  -4  -3  -2  -1  0  1  2  3  4  5  6  7  8  9  10
  0   0   0   0   0  0  1  2  3  0  0  0  0  0  0   0

julia> hcat(dom,map(x->boundaryExtension([1; 2; 3],x,ConstantBE),dom))'
2×16 adjoint(::Matrix{Int64}) with eltype Int64:
 -5  -4  -3  -2  -1  0  1  2  3  4  5  6  7  8  9  10
  1   1   1   1   1  1  1  2  3  3  3  3  3  3  3   3

julia> hcat(dom,map(x->boundaryExtension([1; 2; 3],x,PeriodicBE),dom))'
2×16 adjoint(::Matrix{Int64}) with eltype Int64:
 -5  -4  -3  -2  -1  0  1  2  3  4  5  6  7  8  9  10
  1   2   3   1   2  3  1  2  3  1  2  3  1  2  3   1

julia> hcat(dom,map(x->boundaryExtension([1; 2; 3],x,MirrorBE),dom))'
2×16 adjoint(::Matrix{Int64}) with eltype Int64:
 -5  -4  -3  -2  -1  0  1  2  3  4  5  6  7  8  9  10
  3   2   1   2   3  2  1  2  3  2  1  2  3  2  1   2

```
