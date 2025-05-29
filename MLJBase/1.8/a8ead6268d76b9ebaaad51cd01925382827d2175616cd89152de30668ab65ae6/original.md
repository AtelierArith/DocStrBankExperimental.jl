```
restrict(X, folds, i)
```

The restriction of `X`, a vector, matrix or table, to the `i`th fold of `folds`, where `folds` is a tuple of vectors of row indices.

The method is curried, so that `restrict(folds, i)` is the operator on data defined by `restrict(folds, i)(X) = restrict(X, folds, i)`.

### Example

# 

```julia
folds = ([1, 2], [3, 4, 5],  [6,])
restrict([:x1, :x2, :x3, :x4, :x5, :x6], folds, 2) # [:x3, :x4, :x5]
```

See also [`corestrict`](@ref)
