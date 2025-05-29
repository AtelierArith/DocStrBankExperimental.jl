```
HasDimNames(img) -> HasDimNames{::Bool}
```

Returns the trait `HasDimNames`, indicating whether `x` has named dimensions. Types returning `HasDimNames{true}()` should also have a `names` method that returns a tuple of symbols for each dimension.
