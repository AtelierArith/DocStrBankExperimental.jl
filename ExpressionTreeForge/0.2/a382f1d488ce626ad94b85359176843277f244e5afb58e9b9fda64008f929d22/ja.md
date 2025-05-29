```
set_bounds!(tree::Type_expr_tree, bound_tree::Bound_tree)
set_bounds!(complete_tree::Complete_expr_tree)
```

`bound_tree`の境界を設定するには、`tree`を歩き、葉から根に向かって境界の計算を伝播させます。`Complete_expr_tree`は事前にコンパイルされた`bound_tree`を含んでいるため、単独で使用することができます。
