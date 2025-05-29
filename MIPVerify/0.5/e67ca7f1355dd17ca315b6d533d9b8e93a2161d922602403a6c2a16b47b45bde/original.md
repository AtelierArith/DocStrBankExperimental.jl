```julia
get_conv_params(
    param_dict,
    layer_name,
    expected_size;
    matrix_name,
    bias_name,
    expected_stride,
    padding
)

```

Helper function to import the parameters for a convolution layer from `param_dict` as a     [`Conv2d`](@ref) object.

The default format for the key is `'layer_name/weight'` and `'layer_name/bias'`;     you can customize this by passing in the named arguments `matrix_name` and `bias_name`     respectively. The expected parameter names will then be `'layer_name/matrix_name'`     and `'layer_name/bias_name'`

# Arguments

  * `param_dict::Dict{String}`: Dictionary mapping parameter names to array of weights   / biases.
  * `layer_name::String`: Identifies parameter in dictionary.
  * `expected_size::NTuple{4, Int}`: Tuple of length 4 corresponding to the expected size   of the weights of the layer.
