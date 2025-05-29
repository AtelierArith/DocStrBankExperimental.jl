```
mapsetview(X; prop=f, ...)
```

Like `mapset`, but returns a view instead of a copy.

When possible (eg `X isa StructArray`): uses an optimized approach, keeping all other component untouched. 
