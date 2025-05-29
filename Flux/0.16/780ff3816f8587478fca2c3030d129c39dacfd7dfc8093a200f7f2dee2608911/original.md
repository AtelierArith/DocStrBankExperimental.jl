```
Conv(filter, in => out, σ = identity;
     stride = 1, pad = 0, dilation = 1, groups = 1, [bias, init])
Conv(weight, [bias, activation; stride, pad, dilation])
```

Standard convolutional layer. `filter` is a tuple of integers specifying the size of the convolutional kernel; `in` and `out` specify the number of input and output channels.

Image data should be stored in WHCN order (width, height, channels, batch). In other words, a 100×100 RGB image would be a `100×100×3×1` array, and a batch of 50 would be a `100×100×3×50` array. This has `N = 2` spatial dimensions, and needs a kernel size like `(5,5)`, a 2-tuple of integers.

To take convolutions along `N` feature dimensions, this layer expects as input an array with `ndims(x) == N+2`, where `size(x, N+1) == in` is the number of input channels, and `size(x, ndims(x))` is (as always) the number of observations in a batch. Then:

  * `filter` should be a tuple of `N` integers.
  * Keywords `stride` and `dilation` should each be either single integer, or a tuple with `N` integers.
  * Keyword `pad` specifies the number of elements added to the borders of the data array. It can be

      * a single integer for equal padding all around,
      * a tuple of `N` integers, to apply the same padding at begin/end of each spatial dimension,
      * a tuple of `2*N` integers, for asymmetric padding, or
      * the singleton `SamePad()`, to calculate padding such that `size(output,d) == size(x,d) / stride` (possibly rounded) for each spatial dimension.
  * Keyword `groups` is expected to be an `Int`. It specifies the number of groups to divide a convolution into.

Keywords to control initialization of the layer:

  * `init` - Function used to generate initial weights. Defaults to `glorot_uniform`.
  * `bias` - The initial bias vector is all zero by default. Trainable bias can be disabled entirely by setting this to `false`, or another vector can be provided such as `bias = randn(Float32, out)`.

The second form of the constructor allows you to pass in a pre-constructed weight matrix and bias vector. This is useful when you want to initialize the weights yourself.

See also [`ConvTranspose`](@ref), [`DepthwiseConv`](@ref), [`CrossCor`](@ref).

# Examples

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50); # a batch of 50 RGB images

julia> layer = Conv((5,5), 3 => 7, relu; bias = false)
Conv((5, 5), 3 => 7, relu, bias=false)  # 525 parameters

julia> layer(xs) |> size
(96, 96, 7, 50)

julia> Conv((5,5), 3 => 7; stride = 2)(xs) |> size
(48, 48, 7, 50)

julia> Conv((5,5), 3 => 7; stride = 2, pad = SamePad())(xs) |> size
(50, 50, 7, 50)

julia> Conv((1,1), 3 => 7; pad = (20,10,0,0))(xs) |> size
(130, 100, 7, 50)

julia> Conv((5,5), 3 => 7; stride = 2, dilation = 4)(xs) |> size
(42, 42, 7, 50)
```

```jldoctest
julia> weight = rand(Float32, 3, 4, 5);

julia> bias = zeros(Float32, 5);

julia> layer = Conv(weight, bias, sigmoid)  # expects 1 spatial dimension
Conv((3,), 4 => 5, σ)  # 65 parameters

julia> layer(randn(Float32, 100, 4, 64)) |> size
(98, 5, 64)

julia> Flux.trainables(layer) |> length
2
```
