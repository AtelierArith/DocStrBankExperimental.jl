GradientOp(T::Type; shape::Tuple, dims=1:length(shape))

directional gradient operator along the dimensions `dims` for an array of size `shape`.

# Required Argument

  * `T`                        - type of elements, .e.g. `Float64` for `ComplexF32`

# Required Keyword argument

  * `shape::NTuple{N,Int}`     - shape of the array (e.g., image)

# Optional Keyword argument

  * `dims`                     - dimension(s) along which the gradient is applied; default is `1:length(shape)`
