```
fillup!(::SubsetVectorSolution, pool, random_order)
```

Scans elements from pool and selects those whose inclusion is feasible.

Elements in `pool` must not yet be selected. Parameter `pool` must either be nothing, in which case `x[sel+1:end]` is used as `pool`, or `x[sel+1:_]` for some `_ > sel`. If `random_order` is set, the elements in the pool are processed in random order. Uses `element_added_delta_eval()`. Reorders elements in `pool` so that the selected ones appear in `pool[begin:return-value]`.
