```
localmap!(f, dst, A, B=3; null=zero(eltype(dst)), order=FORWARD_FILTER)
```

set each entry of `dst`, to the result of applying the function `f` to the values of `A` extracted from the neighborhood defined by `B`.

The function `f` is never called with an empty vector of values. Keyword `null` may be used to specify the value of the result where the neighborhood is empty. By default, `null = zero(T)` with `T` the element type of the result.

Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.
