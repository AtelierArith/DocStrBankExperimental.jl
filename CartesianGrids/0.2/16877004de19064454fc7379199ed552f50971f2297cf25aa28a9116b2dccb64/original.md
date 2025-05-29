```
ScalarData <: PointData
```

A wrapper for a one-dimensional array of scalar-valued data. The resulting wrapper can be indexed in the same way as the array itself.

# Constructors

  * `ScalarData(d::AbstractVector[,dtype=Float64])` constructs a wrapper for the one-dimensional array of data `d`
  * `ScalarData(n::Int)` constructs a wrapper for an array of zeros of length `n`.
  * `ScalarData(x::PointData)` constructs a wrapper for an array of zeros of the  same length as that wrapped by `x`.
  * `ScalarData(n::Int,dtype=ComplexF64)` constructs a wrapper for complex-valued data.
  * `ScalarData(x::PointData,dtype=ComplexF64)` constructs a wrapper for an array of  complex zeros of the same length as that wrapped by `x`.

# Example

```jldoctest
julia> f = ScalarData(10);

julia> f[5] = 1.0;

julia> f
10 points of scalar-valued Float64 data
10-element Array{Float64,1}:
 0.0
 0.0
 0.0
 0.0
 1.0
 0.0
 0.0
 0.0
 0.0
 0.0
```
