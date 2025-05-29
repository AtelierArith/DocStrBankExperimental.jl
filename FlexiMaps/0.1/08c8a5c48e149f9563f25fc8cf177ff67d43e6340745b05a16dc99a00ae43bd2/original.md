```
 mapinsert⁻(X; prop=f, ...)
```

Insert `x.prop` with the value `f(x)` into all `x` elements of `X`, and remove the topmost part of `x` that is accessed by `f(x)` (`f` should be an `Accessors` optic). Common usage is for modifying table columns.

Similar to `mapinsert(X; prop=f, ...)`, but also removes a part of `x`.
