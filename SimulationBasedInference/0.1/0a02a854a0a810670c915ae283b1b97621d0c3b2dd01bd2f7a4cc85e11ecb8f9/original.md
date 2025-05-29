```
coordinates(dims...)
```

Converts arguments `dims` to a tuple of coordinate `Dimensions` according to the following rules:

```
- Integers `n` are converted to simple step indices `1:n`
- Vectors are converted to `Dim`s
```
