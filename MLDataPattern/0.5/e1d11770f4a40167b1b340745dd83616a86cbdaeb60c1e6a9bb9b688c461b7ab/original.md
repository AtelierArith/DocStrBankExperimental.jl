```
BufferGetObs(iterator, [buffer])
```

A stateful iterator that stores the output of `iterate(iterator,state)` into `buffer` using `getobs!(buffer, ...)`. Depending on the type of data provided by `iterator` this may be more memory efficient than `getobs(...)`. In the case of array data, for example, this allows for cache-efficient processing of each element without allocating a temporary array.

Note that not all types of data support buffering, because it is the author's choice to opt-in and implement a custom `getobs!`. For those types that do not provide a custom `getobs!`, the buffer will be ignored and the result of `getobs(...)` returned.

see [`eachobs`](@ref) and [`eachbatch`](@ref) for concrete examples.
