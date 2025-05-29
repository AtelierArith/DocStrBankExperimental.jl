```
EliminateGraph <: AbstractGraph
EliminateGraph(tbl::AbstractMatrix) -> EliminateGraph
```

ノード削除を含むアルゴリズムのためのグラフタイプ。このタイプでは、頂点の削除と復元はメモリを割り当てません。コンストラクタの `tbl` は接続のためのブールテーブルです。
