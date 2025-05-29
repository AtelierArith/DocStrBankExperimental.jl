```
stripscalar(x)
```

Dereference value `x`.

If x is a scalar-like object, like a 0-dimensional array or a `Ref`, `stripscalar` returns it's inner value. Otherwise, `x` is returned unchanged.

Useful to strip shaped scalar-like views of their 0-dim array semantics (if present), but leave array-like views unchanged.

Example:

```julia
data = [1, 2, 3]
shape1 = NamedTupleShape(a = ScalarShape{Real}(), b = ArrayShape{Real}(2))
x1 = shape1(data)
@assert x1 isa NamedTuple

shape2 = ArrayShape{Real}(3)
x2 = shape2(data)
@assert x2 isa AbstractArray{Int,1}
```
