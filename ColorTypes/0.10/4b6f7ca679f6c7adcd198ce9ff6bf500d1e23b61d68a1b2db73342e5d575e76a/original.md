`comp1(c)` extracts the first component you'd pass to the constructor of the corresponding object.  For most color types without an alpha channel, this is just the first field, but for types like `BGR` that reverse the internal storage order this provides the value that you'd use to reconstruct the color.

Specifically, for any `Color{T,3}`,

```
c == typeof(c)(comp1(c), comp2(c), comp3(c))
```

returns true.
