```
set_bounds!(tree::Type_expr_tree, bound_tree::Bound_tree)
set_bounds!(complete_tree::Complete_expr_tree)
```

Set the bounds of `bound_tree` by walking `tree` and propagate the bounds' computation from the leaves to the root. As a `Complete_expr_tree` contains a precompiled `bound_tree`, it can be used alone.
