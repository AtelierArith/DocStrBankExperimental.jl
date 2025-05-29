## `transform`

```julia
transform(f::AbstractVector)
transform(img::AbstractMatrix; threaded=true)
transform(vol::AbstractArray{<:Real,3}; threaded=true)
transform(img::AbstractGPUMatrix)
```

Non-in-place squared Euclidean distance transforms that return a new array with the result. They allocate necessary intermediate arrays internally.

  * The first function operates on vectors.
  * The second function operates on matrices with optional threading.
  * The third function operates on 3D arrays with optional threading.
  * The fourth function is specialized for GPU matrices.

The `threaded` parameter can be used to enable or disable parallel computation on the CPU.

#### Arguments

  * `f/img/vol`: Input vector, matrix, or 3D array to be transformed.

#### Examples

```julia
f = rand([0f0, 1f0], 10)
f_bool = boolean_indicator(f)
f_tfm = transform(f_bool)
```
