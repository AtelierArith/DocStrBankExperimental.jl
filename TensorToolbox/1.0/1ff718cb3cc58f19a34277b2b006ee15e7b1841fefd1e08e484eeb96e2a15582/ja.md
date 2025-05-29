```
dimtree(leaves::AbstractVector{<:Integer}[,internal_nodes::AbstractVector{<:Integer}])
dimtree(N[,treetype])
```

次元ツリー。次のものから作成します：

  * 葉のベクトル（および内部ノードのベクトル）、
  * テンソルの次数 N と dimtree のタイプ treetype。デフォルト：treetype="balanced"。
