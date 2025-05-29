```
getobs!(buffer, data, idx)
```

Inplace version of `getobs(data, idx)`. If this method is defined for the type of `data`, then `buffer` should be used to store the result, instead of allocating a dedicated object.

Implementing this function is optional. In the case no such method is provided for the type of `data`, then `buffer` will be *ignored* and the result of [`getobs`](@ref) returned. This could be because the type of `data` may not lend itself to the concept of `copy!`. Thus, supporting a custom `getobs!` is optional and not required.

Custom implementations of `getobs!` should be consistent with [`getobs`](@ref) in terms of the output format, that is `getobs!(buffer, data, idx) == getobs(data, idx)`.

See also [`getobs`](@ref) and [`numobs`](@ref). 
