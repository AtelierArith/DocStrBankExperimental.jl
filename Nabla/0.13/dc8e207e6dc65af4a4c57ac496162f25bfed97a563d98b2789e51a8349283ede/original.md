```
preprocess(f, y, ȳ, xs...) = ()
```

Default implementation of preprocess returns an empty Tuple. Individual sensitivity implementations should add methods specific to their use case. The output is passed in to `∇` as the 3rd or 4th argument in the new-x̄ and update-x̄ cases respectively.

`preprocess` is invoked with `y` and `xs` still boxed. The default implementation just calls `unbox` on them then calls `preprocess` on the unboxed values. If for preprocessing you need the boxed values you should overload `preprocess(f, y::Node, ȳ, xs...)`. If you need them unboxed, then overloading `preprocess(f, y, ȳ, xs...)` is fine.
