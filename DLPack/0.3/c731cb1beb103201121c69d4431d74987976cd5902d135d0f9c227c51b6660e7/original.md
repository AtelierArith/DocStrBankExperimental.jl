```
DLPack
```

The `DLPack` module provides a Julia interface to facilitate bidirectional data exchange of tensor objects between Julia and Python libraries such as JAX, CuPy, PyTorch, among others (all python libraries supporting the [DLPack protocol][1]).

It can share and wrap CPU and CUDA arrays, and supports interfacing through both `PyCall` and `PythonCall`.

[1]: https://data-apis.org/array-api/latest/design*topics/data*interchange.html
