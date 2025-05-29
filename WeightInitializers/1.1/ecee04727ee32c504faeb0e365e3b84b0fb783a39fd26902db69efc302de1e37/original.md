```
identity_init([::AbstractRNG=Utils.default_rng()], [T=Float32], size...; gain::Number=1,
    shift::Union{Integer, Tuple{Integer, Integer}}=0) -> AbstractArray{T}
```

Constructs an array that aims to provide an identity mapping when used as parameters in most layers of a neural network. The identity mapping is scaled by the `gain` parameter.

# Behavior

  * 1D: Returns a `Vector` of zeros (useful for biases in layers where `input_size == output_size`).
  * 2D: Returns an identity matrix (useful for fully connected layers with equal input and output sizes).
  * More than 2D: Returns a tensor where the central slice along the last two dimensions is an identity matrix, and the rest are zeros (useful for convolutional layers, simulating an identity convolution).

# Caveats

  * Not all layers will result in an identity mapping when using this initializer. Exceptions include recurrent and normalization layers.
  * Layers must have `input_size == output_size` for a perfect identity mapping. In cases where this condition is not met, the function pads extra dimensions with zeros.
  * For convolutional layers to achieve an identity mapping, kernel sizes must be odd, and appropriate padding must be applied to ensure the output feature maps are the same size as the input feature maps.

# Arguments

  * `rng::AbstractRNG`: An optional random number generator, included for consistency with other initializers but ignored since the output is deterministic.
  * `T::Type{<:Number}`: The numeric type of the array elements.
  * `size...`: The dimensions of the array to be initialized.
  * `gain::Number=1`: A scaling factor applied to the identity mapping.
  * `shift::Union{Integer, Tuple{Integer, Integer}}=0`: An integer or a tuple specifying the circular shift applied to the output array.

# Returns

  * `AbstractArray{T}`: An array initialized to represent an identity mapping, scaled by `gain` and optionally shifted by `shift`.

# Examples

```jldoctest
julia> identity_init(Xoshiro(123), Float32, 5, 5)
5×5 Matrix{Float32}:
 1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0

julia> identity_init(Xoshiro(123), Float32, 3, 3, 1, 1; gain=1.5)
3×3×1×1 Array{Float32, 4}:
[:, :, 1, 1] =
 0.0  0.0  0.0
 0.0  1.5  0.0
 0.0  0.0  0.0
```
