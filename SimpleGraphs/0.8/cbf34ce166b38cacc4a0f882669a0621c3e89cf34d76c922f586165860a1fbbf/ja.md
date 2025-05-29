`bisect(G::UndirectedGraph)` は、グラフのラプラシアン行列の2番目に小さい固有値に関連付けられた固有ベクトルを使用して、`G` の頂点集合を分割します（以下では `x` と呼ばれます）。

これは次のように呼び出すことができます：

  * `bisect(G,"user",pivot)` は、`x[v] >= pivot` と `x[v] < pivot` に応じて頂点 `v` を分割します。
  * `bisect(G,"zero")` は `bisect(G,"user", 0.0)` と同じです。
  * `bisect(G,"median")` は `bisect(G,"user",m)` と同等で、ここで `m` は `x` の中央値です。
  * `bisect(G,"equal")` は、2つの部分のサイズが最大1だけ異なるように分割を作成します。

`bisect(G)` の単純な呼び出しは、`bisect(G,"zero")` と同等です（これは `bisect(G,"user", 0.0)` と同じです）。
