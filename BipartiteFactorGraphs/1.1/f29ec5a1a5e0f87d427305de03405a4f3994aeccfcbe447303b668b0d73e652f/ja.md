```
add_edge!(g::BipartiteFactorGraph{TVar,TFac,E}, var::Int, fac::Int, data::E) where {TVar,TFac,E}
```

変数ノード `var` と因子ノード `fac` の間にエッジを追加し、関連データを設定します。ユーザーは `var` が変数ノードであり、`fac` が因子ノードであることを確認する必要があります。エッジデータは元の頂点の順序（var, fac）で保存されますが、get*edge*dataを使用して任意の順序でアクセスできます。
