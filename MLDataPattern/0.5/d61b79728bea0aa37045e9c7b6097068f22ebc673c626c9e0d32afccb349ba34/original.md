```
kfolds(data, [k = 5], [obsdim]) -> FoldsView
```

Repartition a `data` container `k` times using a `k` folds strategy and return the sequence of folds as a lazy [`FoldsView`](@ref). The resulting `FoldsView` can then be indexed into or iterated over. Either way, only data subsets are created. That means that no actual data is copied until [`getobs`](@ref) is invoked.

Conceptually, a k-folds repartitioning strategy divides the given `data` into `k` roughly equal-sized parts. Each part will serve as validation set once, while the remaining parts are used for training. This results in `k` different partitions of `data`.

In the case that the size of the dataset is not dividable by the specified `k`, the remaining observations will be evenly distributed among the parts.

```julia
for (x_train, x_val) in kfolds(X, k = 10)
    # code called 10 times
    # nobs(x_val) may differ up to ±1 over iterations
end
```

Multiple variables are supported (e.g. for labeled data)

```julia
for ((x_train, y_train), val) in kfolds((X, Y), k = 10)
    # ...
end
```

By default the folds are created using static splits. Use [`shuffleobs`](@ref) to randomly assign observations to the folds.

```julia
for (x_train, x_val) in kfolds(shuffleobs(X), k = 10)
    # ...
end
```

see [`FoldsView`](@ref) for more info, or [`leaveout`](@ref) for a related function.
