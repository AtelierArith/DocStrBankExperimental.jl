```
layers(::R) where {R <: RasterData}
```

This method controls whether the dataset has named layers. If this is `nothing` (the default), it means that the dataset will have a single layer.

An overload of this method is *required* when there are multiple layers available, and *must* return a `Vector`, usually of `String`. Note that by default, the layers can also be accessed by using an `Integer`, in which case `layer=i` will be the *i*-th entry in `layers(data)`.

Any dataset with a return value that is not `nothing` *must* accept the `layer` keyword.
