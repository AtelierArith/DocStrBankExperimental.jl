```
Maxout(layers...)
Maxout(; layers...)
Maxout(f::Function, n_alts::Int)
```

This contains a number of internal layers, each of which receives the same input. Its output is the elementwise maximum of the the internal layers' outputs.

Maxout over linear dense layers satisfies the universal approximation theorem [goodfellow2013maxout](@cite).

See also [`Parallel`](@ref) to reduce with other operators.

## Arguments

  * Layers can be specified in three formats:

      * A list of `N` Lux layers
      * Specified as `N` keyword arguments.
      * A no argument function `f` and an integer `n_alts` which specifies the number of layers.

# Extended Help

## Inputs

  * `x`: Input that is passed to each of the layers

## Returns

  * Output is computed by taking elementwise `max` of the outputs of the individual layers.
  * Updated state of the `layers`

## Parameters

  * Parameters of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)

## States

  * States of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)
