```
flow_cutter(G::lg.AbstractGraph, time::Integer=10; seed::Integer=-1)
```

`G` の木幅が最小の木分解を見つけるために、`time` 秒間フローカッターアルゴリズムを実行します。

木分解は、以下のキーと値のペアを持つ辞書で返されます：

  * `:treewidth` => 木分解の木幅、
  * `:num_bags` => 木分解のバッグの数、
  * `:num_vertices` グラフ `G` の頂点の数、
  * `:b_n` => 分解の n 番目のバッグ（n は 1 からバッグの数までの整数）。バッグは `G` の頂点の配列です。
  * `:edges` => 木分解のエッジを示す整数ペアの配列。
  * `:comments` => フローカッターによって作成されたヒューリスティックに関するコメントと、分解を見つけるのに十分な時間があったかどうかに関するコメントの配列。

フローカッターアルゴリズムと木分解を見つける方法については、Michael Hamann と Ben Strasser の以下の論文で説明されています：

Graph Bisection with Pareto Optimization - https://dl.acm.org/doi/10.1145/3173045 Computing Tree Decompositions with FlowCutter - https://arxiv.org/abs/1709.08949

# キーワード

  * `seed::Integer=-1`: フローカッターによって使用されるシード。非負の整数でなければならず、そうでない場合はフローカッターによってシードが設定されます。
