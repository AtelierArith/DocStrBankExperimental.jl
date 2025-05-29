```
@searchmethods x
@searchmethods ::X
```

Interactively search through `methodswith(typeof(x))` or `methodswith(X)`.

# Examples

```julia
@searchmethods 1         # search methods defined for integer
@searchmethods ::Int     # search methods defined for a specified type
```
