## `transform!`

```julia
transform!(f::AbstractVector, output, v, z)
transform!(img::AbstractMatrix, output, v, z; threaded=true)
transform!(vol::AbstractArray{<:Real,3}, output, v, z, temp; threaded=true)
transform!(img::AbstractGPUMatrix, output, v, z)
```

In-place squared Euclidean distance transforms. These functions apply the transform to the input data and store the result in the `output` argument.

  * The first function operates on vectors.
  * The second function operates on matrices with optional threading.
  * The third function operates on 3D arrays with optional threading.
  * The fourth function is specialized for GPU matrices.

The intermediate arrays `v` and `z` (and `temp` for 3D arrays) are used for computation. The `threaded` parameter enables parallel computation on the CPU.

#### Arguments

  * `f`: Input vector, matrix, or 3D array.
  * `output`: Preallocated array to store the result.
  * `v`: Preallocated array for indices, matching the dimensions of `f`.
  * `z`: Preallocated array for intermediate values, one element larger than `f`.
  * `temp`: Preallocated array for intermediate values when transforming 3D arrays, matching the dimensions of `output`.

#### Examples

```julia
f = rand([0f0, 1f0], 10)
f_bool = boolean_indicator(f)
output = similar(f)
v = ones(Int32, size(f))
z = ones(eltype(f), size(f) .+ 1)
transform!(f_bool, output, v, z)
```
