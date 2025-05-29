# Extended help

```
constraints_list(am::AbstractAffineMap)
```

### Notes

We assume that the underlying set `X` is polyhedral, i.e., offers a method `constraints_list(X)`.

### Algorithm

This implementation uses the `constraints_list` method to compute the list of constraints of the translation of a lazy [`LinearMap`](@ref).
