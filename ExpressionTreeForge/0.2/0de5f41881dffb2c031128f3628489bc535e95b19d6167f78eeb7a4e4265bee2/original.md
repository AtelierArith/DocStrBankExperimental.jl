```
convexity_status = get_convexity_status(convexity_tree::M_convexity_detection.Convexity_tree)
convexity_status = get_convexity_status(complete_tree::Complete_expr_tree)
```

Return the convexity status of either a `convexity_tree` or a `complete_tree`. The status can be:

  * `constant`
  * `linear`
  * `convex`
  * `concave`
  * `unknown`
