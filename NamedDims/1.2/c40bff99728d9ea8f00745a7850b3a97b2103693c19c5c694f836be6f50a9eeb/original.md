```
dim(dimnames, name)
```

For `dimnames` being a tuple of names (symbols) for the dimensions. and `name` being a one of those names This returns the dimension corresponding to that `name`, e.g. `dim((:a, :b), :b) == 2` If that `name` is not one of the given `dimnames` then an error is thrown.
