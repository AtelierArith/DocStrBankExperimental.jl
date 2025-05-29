```
flipgraph_modular(D::DeltaComplex; kwargs..)
```

閉じた向き付け可能な表面を定義する*Δ-複体* `D` のための**モジュラー フリップ グラフ**を構築します。  

# 引数

  * `labeled_points :: Bool = true` : `false` に設定されている場合、同型は点の名前変更も含まれます。
  * `depth :: Integer = ∞` : フリップグラフが構築される深さを決定します。すなわち、`D` からの距離の上限です。
