```
default_backend(x)
```

Select the recommended backend for an array `x`. This allows to write generic code that works for both CPU and GPU arrays.

The default backend for CPU arrays is currently `PolyesterBackend()`. For GPU arrays, the respective `KernelAbstractions.Backend` is returned.
