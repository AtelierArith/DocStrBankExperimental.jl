```
FluxLayer(layer)
```

Serves as a compatibility layer between Flux and Lux. This uses `Optimisers.destructure` API internally.

!!! warning
    Lux was written to overcome the limitations of `destructure` + `Flux`. It is recommended to rewrite your layer in Lux instead of using this layer.


!!! warning
    Introducing this Layer in your model will lead to type instabilities, given the way `Optimisers.destructure` works.


## Arguments

  * `layer`: Flux layer

## Parameters

  * `p`: Flattened parameters of the `layer`
