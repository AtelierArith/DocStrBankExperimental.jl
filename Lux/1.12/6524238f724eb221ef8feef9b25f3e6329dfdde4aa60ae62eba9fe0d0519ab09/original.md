```
SkipConnection(layers, connection; name=nothing)
SkipConnection(; layers, connection, name=nothing)
```

Create a skip connection which consists of a layer or [`Chain`](@ref) of consecutive layers and a shortcut connection linking the block's input to the output through a user-supplied 2-argument callable. The first argument to the callable will be propagated through the given `layer` while the second is the unchanged, "skipped" input.

The simplest "ResNet"-type connection is just `SkipConnection(layer, +)`.

## Arguments

  * `layer`: Layer or `Chain` of layers to be applied to the input
  * `connection`:

      * A 2-argument function that takes `layer(input)` and the input OR
      * An AbstractLuxLayer that takes `(layer(input), input)` as input

# Extended Help

## Inputs

  * `x`: Will be passed directly to `layer`

## Returns

  * Output of `connection(layer(input), input)`
  * Updated state of `layer`

## Parameters

  * Parameters of `layer` OR
  * If `connection` is an AbstractLuxLayer, then NamedTuple with fields `:layers` and `:connection`

## States

  * States of `layer` OR
  * If `connection` is an AbstractLuxLayer, then NamedTuple with fields `:layers` and `:connection`

See [`Parallel`](@ref) for a more general implementation.
