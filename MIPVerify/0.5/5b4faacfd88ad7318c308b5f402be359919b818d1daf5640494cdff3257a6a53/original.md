```julia
get_matrix_params(
    param_dict,
    layer_name,
    expected_size;
    matrix_name,
    bias_name
)

```

Helper function to import the parameters for a layer carrying out matrix multiplication     (e.g. fully connected layer / softmax layer) from `param_dict` as a     [`Linear`](@ref) object.

The default format for the key is `'layer_name/weight'` and `'layer_name/bias'`;     you can customize this by passing in the named arguments `matrix_name` and `bias_name`     respectively. The expected parameter names will then be `'layer_name/matrix_name'`     and `'layer_name/bias_name'`

# Arguments

  * `param_dict::Dict{String}`: Dictionary mapping parameter names to array of weights   / biases.
  * `layer_name::String`: Identifies parameter in dictionary.
  * `expected_size::NTuple{2, Int}`: Tuple of length 2 corresponding to the expected size  of the weights of the layer.
