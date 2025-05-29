```
Clamp([; min::Maybe{StorageReal} = nothing, max::Maybe{StorageReal} = nothing])
```

Element-wise operation that converts every element to a value inside a range.

**Parameters**

`min` - If specified, values lower than this will be increased to this value.

`max` - If specified, values higher than this will be increased to this value.

!!! note
    At least one of `min` and `max` must be specified.

