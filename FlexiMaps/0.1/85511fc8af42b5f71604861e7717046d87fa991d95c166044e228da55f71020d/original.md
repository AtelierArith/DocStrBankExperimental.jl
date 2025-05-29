```
mapinsert(X; prop=f, ...)
```

Insert `x.prop` with the value `f(x)` into all `x` elements of `X`. Common usage is for adding table columns.

Equivalent to `map(x -> @insert(x.prop = f(x)), X)`, but supports multiple properties.

When possible (eg `X isa StructArray`): uses an optimized approach, keeping all other component untouched. 
