```
corestrict(X, folds, i)
```

The restriction of `X`, a vector, matrix or table, to the *complement* of the `i`th fold of `folds`, where `folds` is a tuple of vectors of row indices.

The method is curried, so that `corestrict(folds, i)` is the operator on data defined by `corestrict(folds, i)(X) = corestrict(X, folds, i)`.

### Example

```julia
folds = ([1, 2], [3, 4, 5],  [6,])
corestrict([:x1, :x2, :x3, :x4, :x5, :x6], folds, 2) # [:x1, :x2, :x6]
```
