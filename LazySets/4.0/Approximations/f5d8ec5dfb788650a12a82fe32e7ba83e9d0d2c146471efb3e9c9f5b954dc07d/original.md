```
overapproximate(S::LazySet, T::Type{<:LazySet}, [args]...; [kwargs]...)
```

Default overapproximation method that falls back to `convert`.

### Input

  * `X`       – set
  * `Type{S}` – target set type
  * `args`    – further arguments
  * `kwargs`  – further keyword arguments

### Output

The result of `convert`, or a `MethodError` if no such method exists.
