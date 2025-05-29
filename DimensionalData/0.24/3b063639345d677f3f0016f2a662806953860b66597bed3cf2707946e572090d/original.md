```
broadcast_dims(f, sources::AbstractDimArray...) => AbstractDimArray
```

Broadcast function `f` over the `AbstractDimArray`s in `sources`, permuting and reshaping dimensions to match where required. The result will contain all the dimensions in  all passed in arrays in the order in which they are found.

## Arguments

  * `sources`: `AbstractDimArrays` to broadcast over with `f`.

This is like broadcasting over every slice of `A` if it is sliced by the dimensions of `B`.
