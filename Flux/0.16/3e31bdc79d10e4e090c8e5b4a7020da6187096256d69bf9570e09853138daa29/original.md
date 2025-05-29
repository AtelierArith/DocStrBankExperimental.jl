```
DepthwiseConv(filter, in => out, σ=identity; stride=1, pad=0, dilation=1, [bias, init])
DepthwiseConv(weight::AbstractArray, [bias, activation; stride, pad, dilation])
```

Return a depthwise convolutional layer, that is a [`Conv`](@ref) layer with number of groups equal to the number of input channels.

See [`Conv`](@ref) for a description of the arguments.

# Examples

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # a batch of 50 RGB images

julia> layer = DepthwiseConv((5,5), 3 => 6, relu; bias=false)
Conv((5, 5), 3 => 6, relu, groups=3, bias=false)  # 150 parameters 

julia> layer(xs) |> size
(96, 96, 6, 50)

julia> DepthwiseConv((5, 5), 3 => 9, stride=2, pad=2)(xs) |> size
(50, 50, 9, 50)
```
