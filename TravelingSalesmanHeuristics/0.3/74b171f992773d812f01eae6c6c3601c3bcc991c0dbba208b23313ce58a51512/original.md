```
cheapest_insertion(distmat::Matrix, initpath::AbstractArray{Int})
```

Given a distance matrix and an initial path, complete the tour by repeatedly doing the cheapest insertion. Return a tuple `(path, cost)`. The initial path must have length at least 2, but can be simply `[i, i]` for some city index `i` which corresponds to starting with a loop at city `i`.

!!! note
    Insertions are always in the interior of the current path so this heuristic can also be used for non-closed TSP paths.


Currently the implementation is a naive $n^3$ algorithm.
