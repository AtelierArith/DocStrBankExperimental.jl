```
BranchLayer(layers...)
BranchLayer(; name=nothing, layers...)
```

Takes an input `x` and passes it through all the `layers` and returns a tuple of the outputs.

## Arguments

  * Layers can be specified in two formats:

      * A list of `N` Lux layers
      * Specified as `N` keyword arguments.

# Extended Help

## Inputs

  * `x`: Will be directly passed to each of the `layers`

## Returns

  * Tuple: `(layer_1(x), layer_2(x), ..., layer_N(x))`  (naming changes if using the kwargs API)
  * Updated state of the `layers`

## Parameters

  * Parameters of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)

## States

  * States of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)

!!! tip "Comparison with Parallel"
    This is slightly different from [`Parallel(nothing, layers...)`](@ref)

      * If the input is a tuple, `Parallel` will pass each element individually to each layer.
      * `BranchLayer` essentially assumes 1 input comes in and is branched out into `N` outputs.


## Example

An easy way to replicate an input to an NTuple is to do

```jldoctest
julia> BranchLayer(NoOpLayer(), NoOpLayer(), NoOpLayer())
BranchLayer(
    layer_1 = NoOpLayer(),
    layer_2 = NoOpLayer(),
    layer_3 = NoOpLayer(),
)         # Total: 0 parameters,
          #        plus 0 states.
```
