```
eachobsparallel(data; useprimary = false, buffered = true)
```

Parallel data iterator for data container `data`. Loads data on all available threads (except the first if `useprimary` is `false`).

If `buffered` is `true`, uses `getobs!` to load samples inplace.

See also `MLDataPattern.eachobs`

!!! warning "Order"
    `eachobsparallel` does not guarantee that the samples are returned in the correct order.

