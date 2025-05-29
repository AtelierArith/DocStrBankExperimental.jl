```
info(X)
```

Return a named-tuple of trait values for `X`, keyed on the names of traits that are meaningful for the object.

*Note on overloading.* This method can be overloaded directly, as in `info(X::SomeAbstractType) = ...`.
