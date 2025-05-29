```
set_convexity!(tree::Type_expr_tree, convexity_tree::Convexity_tree, bound_tree::Bound_tree)
set_convexity!(complete_tree::Complete_expr_tree)
```

基本的なルールから`tree`ノードまたは`complete_tree`ノードの凸性ステータスを推測します。`complete_tree`は境界ツリーを格納しており、凸性検出を単独で実行できますが、`tree`は`bound_tree`（`create_bounds_tree`を参照）および`convexity_tree`（`create_convex_tree`を参照）を必要とします。
