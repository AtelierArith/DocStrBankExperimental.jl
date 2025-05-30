```
greedy_treewidth_deletion(G::LabeledGraph, m::Int=4;
                          score_function::Symbol=:tree_trimming, 
                          elim_order::Array{Symbol, 1}=[])
```

Gから選択したスコア関数を最小化するように貪欲に頂点を削除します。削減されたグラフと削除された頂点の配列を返します。

中間の削除順序と中間グラフの対応する木幅も、Gのために削除順序が提供されている場合に返されます。

このアルゴリズムは、Schutski et alによってPhys. Rev. A 102, 062614で説明されています。

# キーワード

  * `score_function::Symbol=:tree_trimming`: 頂点を削除する際に最大化する関数。                                          (:degree, :direct*treewidth, :tree*trimming)
  * `elim_order::Array{Symbol, 1}=Symbol[]`: direct_treewidthスコア関数で使用されるGの削除順序。
