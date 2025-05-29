```
overapproximate(X::S, ::Type{S}, args...) where {S<:LazySet}
```

Overapproximating a set of type `S` with type `S` is a no-op.

### Input

  * `X`       – set
  * `Type{S}` – target set type
  * `args`    – further arguments (ignored)
  * `kwargs`  – further keyword arguments (ignored)

### Output

The input set.
