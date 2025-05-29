```
set_convexity!(tree::Type_expr_tree, convexity_tree::Convexity_tree, bound_tree::Bound_tree)
set_convexity!(complete_tree::Complete_expr_tree)
```

Deduce from elementary rules the convexity status of `tree` nodes or `complete_tree` nodes. `complete_tree` stores a bounds tree and can run the convexity detection standalone whereas `tree`  requires the `bound_tree` (see `create_bounds_tree`) and `convexity_tree` (see `create_convex_tree`).
