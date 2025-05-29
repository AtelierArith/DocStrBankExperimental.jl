```
order([::Type{T} = BigInt, ]M::Monoid) where T
```

Return the order of `M` as an instance of `T`. If `M` is of infinite order, `GroupsCore.InfiniteOrder` exception will be thrown.

!!! warning
    Only arbitrary sized integers are required to return a mathematically correct answer.

