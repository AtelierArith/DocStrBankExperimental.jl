```
convexity_status = get_convexity_status(convexity_tree::M_convexity_detection.Convexity_tree)
convexity_status = get_convexity_status(complete_tree::Complete_expr_tree)
```

`convexity_tree` または `complete_tree` のいずれかの凸性状態を返します。状態は次のいずれかです：

  * `constant`
  * `linear`
  * `convex`
  * `concave`
  * `unknown`
