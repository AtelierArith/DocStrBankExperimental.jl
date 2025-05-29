```
modify(f, series::AbstractRasterSeries)
```

Apply function `f` to the data of the child object. If the child is an `AbstractRasterStack` the function will be passed on to its child `AbstractRaster`s.

`f` must return an identically sized array.

This method triggers a complete rebuild of all objects, and disk based objects will be transferred to memory.

An example of the usefulnesss of this is for swapping out array backend for an entire series to `CuArray` from CUDA.jl to copy data to a GPU.
