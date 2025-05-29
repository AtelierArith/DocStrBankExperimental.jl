```
Complete_expr_tree{T} <: AbstractTree
```

Implementation of an expression tree. `Complete_expr_tree` is the same than `Type_expr_tree` with the additions in each node of a `Bounds` and `Convexity_wrapper`. A `Complete_expr_tree` has fields:

  * `field::Complete_node{T}` representing an operator, a constant or a variable alongide its bounds and its convexity status;
  * `children::Vector{Complete_expr_tree{T}}` a vector of children, each of them being a `Complete_expr_tree{T}`.
