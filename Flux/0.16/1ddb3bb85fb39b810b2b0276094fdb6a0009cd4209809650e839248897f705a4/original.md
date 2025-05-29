```
ConvTranspose(filter, in => out, σ=identity; stride=1, pad=0, outpad=0, dilation=1, [bias, init])
ConvTranspose(weight, [bias, activation; stride, pad, outpad, dilation])
```

Standard convolutional transpose layer. `filter` is a tuple of integers specifying the size of the convolutional kernel, while `in` and `out` specify the number of input and output channels.

Note that `pad=SamePad()` here tries to ensure `size(output,d) == size(x,d) * stride`.

To conserve [`Conv`](@ref) inversability when `stride > 1`, `outpad` can be used to increase the size of the output in the desired dimensions. Whereas `pad` is used to zero-pad the input, `outpad` only affects the output shape.

Parameters are controlled by additional keywords, with defaults `init=glorot_uniform` and `bias=true`.

The second form of the constructor allows you to pass in a pre-constructed weight matrix and bias vector. This is useful when you want to initialize the weights yourself.

See also [`Conv`](@ref) for more detailed description of keywords.

# Examples

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # a batch of 50 RGB images

julia> layer = ConvTranspose((5,5), 3 => 7, relu)
ConvTranspose((5, 5), 3 => 7, relu)  # 532 parameters

julia> layer(xs) |> size
(104, 104, 7, 50)

julia> ConvTranspose((5,5), 3 => 7, stride=2)(xs) |> size
(203, 203, 7, 50)

julia> ConvTranspose((5,5), 3 => 7, stride=2, outpad=1)(xs) |> size
(204, 204, 7, 50)

julia> ConvTranspose((5,5), 3 => 7, stride=3, pad=SamePad())(xs) |> size
(300, 300, 7, 50)
```

```jldoctest
julia> weight = rand(Float32, 3, 4, 5);

julia> bias = zeros(Float32, 4);

julia> layer = ConvTranspose(weight, bias, sigmoid)
ConvTranspose((3,), 5 => 4, σ)  # 64 parameters

julia> layer(randn(Float32, 100, 5, 64)) |> size  # transposed convolution will increase the dimension size (upsampling)
(102, 4, 64)

julia> Flux.trainables(layer) |> length
2
```
