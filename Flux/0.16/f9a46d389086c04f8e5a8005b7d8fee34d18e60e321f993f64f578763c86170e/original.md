```
@autosize (size...,) Chain(Layer(_ => 2), Layer(_), ...)
```

Returns the specified model, with each `_` replaced by an inferred number, for input of the given `size`.

The unknown sizes are usually the second-last dimension of that layer's input, which Flux regards as the channel dimension. (A few layers, `Dense` & [`LayerNorm`](@ref), instead always use the first dimension.) The underscore may appear as an argument of a layer, or inside a `=>`. It may be used in further calculations, such as `Dense(_ => _÷4)`.

# Examples

```
julia> @autosize (3, 1) Chain(Dense(_ => 2, sigmoid), BatchNorm(_, affine=false))
Chain(
  Dense(3 => 2, σ),                     # 8 parameters
  BatchNorm(2, affine=false),
) 

julia> img = [28, 28];

julia> @autosize (img..., 1, 32) Chain(              # size is only needed at runtime
          Chain(c = Conv((3,3), _ => 5; stride=2, pad=SamePad()),
                p = MeanPool((3,3)),
                b = BatchNorm(_),
                f = Flux.flatten),
          Dense(_ => _÷4, relu, init=Flux.rand32),   # can calculate output size _÷4
          SkipConnection(Dense(_ => _, relu), +),
          Dense(_ => 10),
       )
Chain(
  Chain(
    c = Conv((3, 3), 1 => 5, pad=1, stride=2),  # 50 parameters
    p = MeanPool((3, 3)),
    b = BatchNorm(5),                   # 10 parameters, plus 10
    f = Flux.flatten,
  ),
  Dense(80 => 20, relu),                # 1_620 parameters
  SkipConnection(
    Dense(20 => 20, relu),              # 420 parameters
    +,
  ),
  Dense(20 => 10),                      # 210 parameters
)         # Total: 10 trainable arrays, 2_310 parameters,
          # plus 2 non-trainable, 10 parameters, summarysize 10.469 KiB.

julia> outputsize(ans, (28, 28, 1, 32))
(10, 32)
```

Limitations:

  * While `@autosize (5, 32) Flux.Bilinear(_ => 7)` is OK, something like `Bilinear((_, _) => 7)` will fail.
  * While `Scale(_)` and `LayerNorm(_)` are fine (and use the first dimension), `Scale(_,_)` and `LayerNorm(_,_)` will fail if `size(x,1) != size(x,2)`.
