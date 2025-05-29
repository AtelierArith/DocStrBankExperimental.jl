```
leavepout(data, p = 1)
```

Repartition a `data` container using a k-fold strategy, where `k` is chosen in such a way, that each validation subset of the resulting folds contains roughly `p` observations. Defaults to `p = 1`, which is also known as "leave-one-out" partitioning.

The resulting sequence of folds is returned as a lazy iterator. Only data subsets are created. That means no actual data is copied until [`getobs`](@ref) is invoked.

```julia
for (train, val) in leavepout(X, p=2)
    # if numobs(X) is dividable by 2,
    # then numobs(val) will be 2 for each iteraton,
    # otherwise it may be 3 for the first few iterations.
end
```

See[`kfolds`](@ref) for a related function.
