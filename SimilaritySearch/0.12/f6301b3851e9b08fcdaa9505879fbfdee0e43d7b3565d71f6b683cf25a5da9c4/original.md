```
struct SearchGraph <: AbstractSearchIndex
```

SearchGraph index. It stores a set of points that can be compared through a distance function `dist`. The performance is determined by the search algorithm `algo` and the neighborhood policy. It supports callbacks to adjust parameters as insertions are made.

  * `hints`: Initial points for exploration (empty hints imply using random points)

Note: Parallel insertions should be made through `append!` or `index!` function with `parallel_block > 1`
