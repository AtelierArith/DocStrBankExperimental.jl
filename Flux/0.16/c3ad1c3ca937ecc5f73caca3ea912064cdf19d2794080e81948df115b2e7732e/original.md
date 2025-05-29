```
identity_init(size...; gain=1, shift=0) -> Array
identity_init(; kw...) -> Function
```

Return an `Array{Float32}` of the given `size` which yields an identity mapping when used as parameters in most Flux layers. Use `gain` to scale the identity by a constant.

Often useful in the context of transfer learning, i.e when one wants to add more capacity to a model but start from the same mapping.

Has the following behaviour

  * 1D: A `Vector` of `zeros` (useful for an identity bias)
  * 2D: An identity matrix (useful for an identity matrix multiplication)
  * More than 2D: A dense block array of center tap spatial filters (useful for an identity convolution)

Some caveats: 

  * Not all layers will be identity mapping when used with this init. Exceptions include recurrent layers and normalization layers.
  * Layers must have `input_size == output_size` for identity mapping to be possible. When this is not the case, extra dimensions of the array are padded with zeros.
  * For convolutional layers, in addition to the above, the kernel sizes must also be odd and padding must be applied so that output feature maps have the same size as input feature maps, e.g by using [`SamePad`](@ref).

Use keyword `shift` (integer or tuple) to apply circular shift to the output, equivalent to `Base.circshift(identity_init(size...), shift)`.

For consistency with other initialisers, it accepts `rng::AbstractRNG` as an optional first argument. But this is ignored, since the result is not random.

# Examples

```jldoctest
julia> Flux.identity_init(3,5)
3×5 Matrix{Float32}:
 1.0  0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0

julia> Dense(5 => 3, relu, init=Flux.identity_init)([1,-2,3,-4,5])
3-element Vector{Float32}:
 1.0
 0.0
 3.0

julia> Flux.identity_init(3,3,2; gain=100)
3×3×2 Array{Float32, 3}:
[:, :, 1] =
   0.0  0.0  0.0
 100.0  0.0  0.0
   0.0  0.0  0.0

[:, :, 2] =
 0.0    0.0  0.0
 0.0  100.0  0.0
 0.0    0.0  0.0

julia> x4 = cat([1 2 3; 4 5 6; 7 8 9]; dims=4);

julia> Conv((2,2), 1 => 1, init=Flux.identity_init(gain=10), pad=SamePad())(x4)
3×3×1×1 Array{Float32, 4}:
[:, :, 1, 1] =
 10.0  20.0  30.0
 40.0  50.0  60.0
 70.0  80.0  90.0
```
