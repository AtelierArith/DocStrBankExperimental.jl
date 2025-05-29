```
HybridArray{Tuple{dims...}}(array)
```

Wraps an `AbstractArray` with a combination of static and dynamic sizes, so to take advantage of the (faster) methods defined by the StaticArrays package. The size is checked once upon construction to determine if the number of elements (`length`) match, but the array may be reshaped.
