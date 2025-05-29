```
product!(out::PointData,p::PointData,q::PointData)
```

Compute the Hadamard (i.e. element by element) product of point data data `p` and `q` and return the result in `out`. Note that `p` and `q` can be of mixed type (scalar, vector, tensor), as long as one of them is a scalar. Also, `out` must have element type that is consistent with the promoted type of `p` and `q`.

# Example

```jldoctest
julia> fcs = ScalarData(5,dtype=ComplexF64);

julia> fill!(fcs,2im)
5 points of scalar-valued Complex{Float64} data
5-element Array{Complex{Float64},1}:
 0.0 + 2.0im
 0.0 + 2.0im
 0.0 + 2.0im
 0.0 + 2.0im
 0.0 + 2.0im

julia> frt = TensorData(fcs,dtype=Float64);

julia> fill!(frt,1.0)
5 points of tensor-valued Float64 data dudx, dudy, dvdx, dvdy
5×4 Array{Float64,2}:
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0

julia> out = similar(frt,element_type=ComplexF64);

julia> product!(out,frt,fcs)
5 points of tensor-valued Complex{Float64} data dudx, dudy, dvdx, dvdy
5×4 Array{Complex{Float64},2}:
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
 0.0+2.0im  0.0+2.0im  0.0+2.0im  0.0+2.0im
```
