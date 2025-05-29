```
broadcast_dims!(f, dest::AbstractDimArray, sources::AbstractDimArray...) => dest
```

Broadcast function `f` over the `AbstractDimArray`s in `sources`, writing to `dest`.  `sources` are permuting and reshaping dimensions to match where required.

The result will contain all the dimensions in all passed in arrays, in the order in which they are found.

## Arguments

  * `dest`: `AbstractDimArray` to update.
  * `sources`: `AbstractDimArrays` to broadcast over with `f`.
