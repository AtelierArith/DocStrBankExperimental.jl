```
flipgraph_modular(g::Integer, p::Integer; kwargs..) :: FlipGraph
```

**モジュラー フリップグラフ**を構築します。これは、`g` の世代を持つ閉じた向きのある表面に `p` の点があるものです。  

# 引数

  * `labeled_points :: Bool = true` : `false` に設定すると、同型は点の名前変更も含まれます。
