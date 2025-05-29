```
similar(static_array)
similar(static_array, T)
similar(array, ::Size)
similar(array, T, ::Size)
```

Constructs and returns a mutable but statically-sized array (i.e. a `StaticArray`). If the input `array` is not a `StaticArray`, then the `Size` is required to determine the output size (or else a dynamically sized array will be returned).
