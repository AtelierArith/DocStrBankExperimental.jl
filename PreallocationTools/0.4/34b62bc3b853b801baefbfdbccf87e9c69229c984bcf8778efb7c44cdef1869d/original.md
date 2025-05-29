```
b = LazyBufferCache(f = identity; initializer! = identity)
```

A lazily allocated buffer object.  Given an array `u`, `b[u]` returns an array of the same type and size `f(size(u))` (defaulting to the same size), which is allocated as needed and then cached within `b` for subsequent usage.

By default the created buffers are not initialized, but a function `initializer!` can be supplied which is applied to the buffer when it is created, for instance `buf -> fill!(buf, 0.0)`.

Optionally, the size can be explicitly given at calltime using `b[u,s]`, which will return a cache of size `s`.
