```
Bilinear((in1, in2) => out, σ=identity; bias=true, init=glorot_uniform)
Bilinear(W::AbstractArray, [bias, σ])
```

Creates a layer which is fully connected between two inputs and the output, and otherwise similar to [`Dense`](@ref). Its output, given vectors `x` & `y`, is another vector `z` with, for all `i ∈ 1:out`:

```
z[i] = σ(x' * W[i,:,:] * y + bias[i])
```

If `x` and `y` are matrices, then each column of the output `z = B(x, y)` is of this form, with `B` the Bilinear layer.

If the second input `y` is not given, it is taken to be equal to `x`, i.e. `B(x) == B(x, x)`

The two inputs may also be provided as a tuple, `B((x, y)) == B(x, y)`, which is accepted as the input to a `Chain`.

If the two input sizes are the same, `in1 == in2`, then you may write `Bilinear(in => out, σ)`.

The initialisation works as for [`Dense`](@ref) layer, with `W = init(out, in1, in2)`. By default the bias vector is `zeros(Float32, out)`, option `bias=false` will switch off trainable bias. Either of these may be provided explicitly.

# Examples

```jldoctest
julia> x, y = randn(Float32, 5, 32), randn(Float32, 5, 32);

julia> B = Flux.Bilinear((5, 5) => 7)
Bilinear(5 => 7)    # 182 parameters

julia> B(x) |> size  # interactions based on one input
(7, 32)

julia> B(x,y) == B((x,y))  # two inputs, may be given as a tuple
true

julia> sc = SkipConnection(
                Chain(Dense(5 => 20, tanh), Dense(20 => 9, tanh)),
                Flux.Bilinear((9, 5) => 3, bias=false),
            );  # used as the recombinator, with skip as the second input

julia> sc(x) |> size
(3, 32)

julia> Flux.Bilinear(rand(4,8,16), false, tanh)  # first dim of weight is the output
Bilinear((8, 16) => 4, tanh; bias=false)  # 512 parameters
```
