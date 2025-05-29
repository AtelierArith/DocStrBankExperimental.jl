```
compute_backward_flow(graph, forward_flow, vertex)
```

この関数は、グラフ内の指定された頂点の逆流を計算します。最初に、頂点の隣接点を見つけ、頂点が隣接点のいずれかの前方流に含まれているかを確認します。含まれていない場合、関数は0を返します。含まれている場合、関数は隣接点の前方流における頂点のインデックスを見つけます。頂点が隣接点の流に含まれていない場合、エラーが発生します。過去の頂点が複数見つかった場合も、エラーが発生します。それ以外の場合、関数は最初の過去の頂点を返します。

# 引数

  * `graph`: グラフ。
  * `forward_flow`: 前方流関数。
  * `vertex`: 逆流を計算するための頂点。

# 戻り値

  * 最初の過去の頂点が存在する場合はそれを返し、存在しない場合は0を返します。

# 例

```julia
graph = Graph(5)
forward_flow = (n -> n + 1)
vertex = 3
backward_flow_vertex = compute_backward_flow(graph, forward_flow, vertex)
```
