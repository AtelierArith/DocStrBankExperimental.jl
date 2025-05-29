```
Chain(layers...; name=nothing)
Chain(; layers..., name=nothing)
```

Collects multiple layers / functions to be called in sequence on a given input.

## Arguments

  * Layers can be specified in two formats:

      * A list of `N` Lux layers
      * Specified as `N` keyword arguments.

# Extended Help

## Inputs

Input `x` is passed sequentially to each layer, and must conform to the input requirements of the internal layers.

## Returns

  * Output after sequentially applying all the layers to `x`
  * Updated model states

## Parameters

  * Parameters of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)

## States

  * States of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)

## Miscellaneous Properties

  * Allows indexing and field access syntax. We can access the `i`th layer by `m[i]` or `m.layer_i`. We can also index using ranges or arrays.

## Example

```jldoctest
julia> Chain(Dense(2, 3, relu), BatchNorm(3), Dense(3, 2))
Chain(
    layer_1 = Dense(2 => 3, relu),      # 9 parameters
    layer_2 = BatchNorm(3, affine=true, track_stats=true),  # 6 parameters, plus 7
    layer_3 = Dense(3 => 2),            # 8 parameters
)         # Total: 23 parameters,
          #        plus 7 states.

julia> Chain(Dense(2, 3, relu), BatchNorm(3), Dense(3, 2); name="MyFancyChain")
MyFancyChain(
    layer_1 = Dense(2 => 3, relu),      # 9 parameters
    layer_2 = BatchNorm(3, affine=true, track_stats=true),  # 6 parameters, plus 7
    layer_3 = Dense(3 => 2),            # 8 parameters
)         # Total: 23 parameters,
          #        plus 7 states.
```
