```
leaveout(data, [size = 1], [obsdim]) -> FoldsView
```

Repartition a `data` container using a k-fold strategy, where `k` is chosen in such a way, that each validation subset of the resulting folds contains roughly `size` observations. Defaults to `size = 1`, which is also known as "leave-one-out" partitioning.

The resulting sequence of folds is returned as a lazy [`FoldsView`](@ref), which can be index into or iterated over. Either way, only data subsets are created. That means no actual data is copied until [`getobs`](@ref) is invoked.

```julia
for (train, val) in leaveout(X, size = 2)
    # if nobs(X) is dividable by 2,
    # then nobs(val) will be 2 for each iteraton,
    # otherwise it may be 3 for the first few iterations.
end
```

see [`FoldsView`](@ref) for more info, or [`kfolds`](@ref) for a related function.
