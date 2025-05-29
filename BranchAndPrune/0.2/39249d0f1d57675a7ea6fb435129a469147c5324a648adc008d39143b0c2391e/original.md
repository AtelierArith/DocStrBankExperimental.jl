```
BranchAndPruneSearch(S, process, bisect, initial_region)
```

Branch and prune search, using the search order `S` on the given initial region. It works by recursively bisecting the regions of search with `bisect` until all regions are found satisfactory according to `process`. Build a binary tree relating the regions to each other as the search progress.

`process` and `bisect` both take a single region as an argument.

`process` must return an action to perform and the region on which to perform it. The possible actions are

  * `:store`: the region is considered as final, is stored, and is not   further processed.
  * `:branch`: the element is bisected and each of the two resulting part   are processed independently.
  * `:prune`: the element is discarded from the tree.   If it is the last descendant of a branch, the whole branch is pruned   from the tree.   The intermediate nodes with a single descendant are also removed from the tree.

The initial region can be returned unchanged if no refinement is possible at this stage.

`bisect` is used when a region is marked to be branched. It must return two subregions of the original one, and of the same type.

`BranchAndPruneSearch` objects are iterable, exhausting the iterable performs the full search.

WARNING By default, the search only ends when all remaining regions are given the directive `:store` by the process function. For stopping based on different criterion, either manually break the iteration loop or use `bpsearch(search ; callback)` with a custom callback function.
