```
Complete_expr_tree{T} <: AbstractTree
```

式木の実装。`Complete_expr_tree`は、各ノードに`Bounds`と`Convexity_wrapper`が追加された`Type_expr_tree`と同じです。`Complete_expr_tree`には以下のフィールドがあります：

  * `field::Complete_node{T}`は演算子、定数、または変数を表し、その境界と凸性の状態を持っています；
  * `children::Vector{Complete_expr_tree{T}}`は子のベクターであり、それぞれが`Complete_expr_tree{T}`です。
