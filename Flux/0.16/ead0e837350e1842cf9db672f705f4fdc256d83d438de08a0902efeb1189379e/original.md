```
CrossCor(filter, in => out, σ=identity; stride=1, pad=0, dilation=1, [bias, init])
CrossCor(weight::AbstractArray, [bias, activation; stride, pad, dilation])
```

Standard cross correlation layer. `filter` is a tuple of integers specifying the size of the convolutional kernel; `in` and `out` specify the number of input and output channels.

Parameters are controlled by additional keywords, with defaults `init=glorot_uniform` and `bias=true`.

The second form of the constructor allows you to pass in a pre-constructed weight matrix and bias vector. This is useful when you want to initialize the weights yourself

See also [`Conv`](@ref) for more detailed description of keywords.

# Examples

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # a batch of 50 RGB images

julia> layer = CrossCor((5,5), 3 => 6, relu; bias=false)
CrossCor((5, 5), 3 => 6, relu, bias=false)  # 450 parameters

julia> layer(xs) |> size
(96, 96, 6, 50)

julia> CrossCor((5,5), 3 => 7, stride=3, pad=(2,0))(xs) |> size
(34, 32, 7, 50)
```

```jldoctest
julia> weight = rand(Float32, 3, 4, 5);

julia> bias = zeros(Float32, 5);

julia> layer = CrossCor(weight, bias, relu)
CrossCor((3,), 4 => 5, relu)  # 65 parameters

julia> layer(randn(Float32, 100, 4, 64)) |> size
(98, 5, 64)
```
