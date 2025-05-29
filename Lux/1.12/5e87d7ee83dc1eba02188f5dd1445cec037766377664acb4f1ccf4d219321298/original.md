```
SimpleChainsLayer(layer, to_array::Union{Bool, Val}=Val(false))
SimpleChainsLayer(layer, lux_layer, to_array)
```

Wraps a `SimpleChains` layer into a `Lux` layer. All operations are performed using `SimpleChains` but the layer satisfies the `AbstractLuxLayer` interface.

`ToArray` is a boolean flag that determines whether the output should be converted to a regular `Array` or not. Default is `false`.

## Arguments

  * `layer`: SimpleChains layer
  * `lux_layer`: Potentially equivalent Lux layer that is used for printing
