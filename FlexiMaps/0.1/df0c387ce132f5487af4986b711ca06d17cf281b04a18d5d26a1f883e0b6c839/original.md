```
mapset(X; prop=f, ...)
```

Set values of `x.prop` to `f(x)` for all `x` elements of `X`. Common usage is for modifying table columns.

Equivalent to `map(x -> @set(x.prop = f(x)), X)`, but supports multiple properties.

When possible (eg `X isa StructArray`): uses an optimized approach, keeping all other component untouched. 
