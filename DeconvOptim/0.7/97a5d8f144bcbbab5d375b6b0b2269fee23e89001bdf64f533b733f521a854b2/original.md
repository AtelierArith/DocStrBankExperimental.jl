```
conv(u, v[, dims])
```

Convolve `u` with `v` over `dims` dimensions with an FFT based method. Note, that this method introduces wrap-around artifacts without proper padding/windowing.

# Arguments

  * `u` is an array in real space.
  * `v` is the array to be convolved in real space as well.
  * Per default `ntuple(+, min(N, M)))` means that we perform the convolution    over all dimensions of that array which has less dimensions.    If `dims` is an array with integers, we perform convolution    only over these dimensions. Eg. `dims=[1,3]` would perform the convolution   over the first and third dimension. Second dimension is not convolved.

If `u` and `v` are both a real valued array we use `rfft` and hence the output is real as well. If either `u` or `v` is complex we use `fft` and output is hence complex.

# Examples

1D with FFT over all dimensions. We choose `v` to be a delta peak. Therefore convolution should act as identity.

```jldoctest
julia> u = [1 2 3 4 5]
1×5 Array{Int64,2}:
 1  2  3  4  5
julia> v = [0 0 1 0 0]
1×5 Array{Int64,2}:
 0  0  1  0  0
julia> conv(u, v)
1×5 Matrix{Float64}:
 4.0  5.0  1.0  2.0  3.0
```

2D with FFT with different `dims` arguments.

```jldoctest
julia> u = 1im .* [1 2 3; 4 5 6]
2×3 Matrix{Complex{Int64}}:
 0+1im  0+2im  0+3im
 0+4im  0+5im  0+6im
julia> v = [1im 0 0; 1im 0 0]
2×3 Matrix{Complex{Int64}}:
 0+1im  0+0im  0+0im
 0+1im  0+0im  0+0im
julia> conv(u, v)
2×3 Matrix{ComplexF64}:
 -5.0+0.0im  -7.0+0.0im  -9.0+0.0im
 -5.0+0.0im  -7.0+0.0im  -9.0+0.0im
```
