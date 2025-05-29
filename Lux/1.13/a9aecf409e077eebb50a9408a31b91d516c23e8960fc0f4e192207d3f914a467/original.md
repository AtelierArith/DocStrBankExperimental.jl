```
PairwiseFusion(connection, layers...; name=nothing)
PairwiseFusion(connection; name=nothing, layers...)
PairwiseFusion(; connection, layers..., name=nothing)
```

```
x1 → layer1 → y1 ↘
                  connection → layer2 → y2 ↘
              x2 ↗                          connection → y3
                                        x3 ↗
```

## Arguments

  * `connection`: Takes 2 inputs and combines them
  * `layers`: `AbstractLuxLayer`s. Layers can be specified in two formats:

      * A list of `N` Lux layers
      * Specified as `N` keyword arguments.

# Extended Help

## Inputs

Layer behaves differently based on input type:

1. If the input `x` is a tuple of length `N + 1`, then the `layers` must be a tuple of length `N`. The computation is as follows

```julia
y = x[1]
for i in 1:N
    y = connection(x[i + 1], layers[i](y))
end
```

2. Any other kind of input

```julia
y = x
for i in 1:N
    y = connection(x, layers[i](y))
end
```

## Returns

  * See Inputs section for how the return value is computed
  * Updated model state for all the contained layers

## Parameters

  * Parameters of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)

## States

  * States of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)
