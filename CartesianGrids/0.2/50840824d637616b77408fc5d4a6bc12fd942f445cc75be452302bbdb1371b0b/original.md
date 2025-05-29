```
CircularConvolution{M, N, T}
```

A preplanned, circular convolution operator on an M × N matrix of data of type T

# Fields

  * `Ĝ`: DFT coefficients of the convolution kernel
  * `F`: preplanned rFFT operator
  * `F⁻¹`: preplanned irFFT operator
  * `nthreads` : optimized number of threads to use, if appropriate
  * `paddedSpace`: scratch space to zero-pad the input matrix
  * `Â`: scratch space to store the DFT coefficients of the zero-padded input matrix

# Constructors:

  * `CircularConvolution(G::Matrix{T})`

# Example:

```jldoctest
julia> G = repeat(1.0:3,1,4)
3×4 Array{Float64,2}:
 1.0  1.0  1.0  1.0
 2.0  2.0  2.0  2.0
 3.0  3.0  3.0  3.0

julia> C = CircularConvolution(G)
Circular convolution on a 3 × 4 matrix of data type Float64

julia> C*reshape(1:12, 3, 4)
3×4 Array{Int64,2}:
 164  164  164  164
 130  130  130  130
 148  148  148  148
```
