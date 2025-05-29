```
NJClust(merges::Matrix{M}, heights::Matrix{H})
```

fields:

  * merges is a n-1 x 2 matrix of integers: absolute values of negative integers indicate index into the distance matrix (i.e., leaves). positive integers are the index into the merge list (i.e., the kth internal node)
  * heights is an n-1 x 2 matrix where each value is the distance from the left (1) or right (2) chield from its parent. Specifically `heights[i,j]` is the `j`th childs distance to the parent node, row `i`.
