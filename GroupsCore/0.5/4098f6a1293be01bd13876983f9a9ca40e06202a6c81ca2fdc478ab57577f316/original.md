```
order(m::MonoidElement)
order(::Type{T}, m::MonoidElement) where T
```

Return the order of `m` as an instance of `T`. If `m` is of infinite order `GroupsCore.InfiniteOrder` exception will be thrown.

!!! warning
    Only arbitrary sized integers are required to return a mathematicaly correct answer.

