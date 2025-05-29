```
VectorData <: PointData
```

A wrapper for a one-dimensional array of two-component vector-valued data. The resulting wrapper can be indexed as though the first component and second component are stacked on top of each other.

# Constructors

  * `VectorData(d::AbstractVector[,dtype=Float64])` constructs a wrapper for the one-dimensional array of data `d`, splitting `d` into the `u` and `v` components evenly.
  * `VectorData(u::AbstractVector,v::AbstractVector)` constructs a wrapper for the vector components data `u` and `v`.
  * `VectorData(n::Int)` constructs a wrapper with zeros of length `n` for both components.
  * `VectorData(x::PointData)` constructs a wrapper for zero components of the  same length as that wrapped by `x`.
  * `VectorData(n::Int,dtype=ComplexF64)` constructs a wrapper with complex-valued zeros  of length `n` for both components.

# Example

```jldoctest
julia> f = VectorData(10,dtype=ComplexF64);

julia> f.v[1:5] = 1:5;

julia> f
10 points of vector-valued Complex{Float64} data
10×2 Array{Complex{Float64},2}:
 0.0+0.0im  1.0+0.0im
 0.0+0.0im  2.0+0.0im
 0.0+0.0im  3.0+0.0im
 0.0+0.0im  4.0+0.0im
 0.0+0.0im  5.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im

julia> f[7] = 1im; f[18] = 0.2;

julia> f
10 points of vector-valued Complex{Float64} data
10×2 Array{Complex{Float64},2}:
 0.0+0.0im  1.0+0.0im
 0.0+0.0im  2.0+0.0im
 0.0+0.0im  3.0+0.0im
 0.0+0.0im  4.0+0.0im
 0.0+0.0im  5.0+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+1.0im  0.0+0.0im
 0.0+0.0im  0.2+0.0im
 0.0+0.0im  0.0+0.0im
 0.0+0.0im  0.0+0.0im
```
