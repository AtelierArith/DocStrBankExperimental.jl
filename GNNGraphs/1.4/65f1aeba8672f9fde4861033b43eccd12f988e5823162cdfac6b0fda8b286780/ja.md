```
rand_temporal_radius_graph(number_nodes::Int, 
                           number_snapshots::Int,
                           speed::AbstractFloat,
                           r::AbstractFloat;
                           self_loops = false,
                           dir = :in,
                           kws...)
```

`number_nodes` ノードと `number_snapshots` スナップショットからなるランダムな時間的グラフを作成します。まず、ノードの位置は単位正方形内でランダムに生成されます。2つのノードは、その距離が与えられた半径 `r` よりも小さい場合に接続されます。次のスナップショットは、新しい位置に対して同じ構造を適用することによって得られます。各スナップショットの新しい点の位置は、前の位置にランダムな独立した変位ベクトルを適用することによって決定されます。変位の方向は均等にランダムに選ばれ、その長さは `[0, speed]` の範囲で均等に選ばれます。次に、接続が再計算されます。点が境界の外に移動した場合、その位置は境界で跳ね返ったかのように更新されます。

# 引数

  * `number_nodes`: 各スナップショットのノードの数。
  * `number_snapshots`: スナップショットの数。
  * `speed`: ノードを更新するための速度。
  * `r`: 接続の半径。
  * `self_loops`: `true` の場合、ノード自身を隣接ノードの中に含め、その場合グラフには自己ループが含まれます。
  * `dir`: エッジの方向。`dir=:in` の場合、エッジは隣接ノードから中心ノードに向かいます。`dir=:out` の場合は逆の方向になります。
  * `kws`: さらなるキーワード引数は、各スナップショットの [`GNNGraph`](@ref) コンストラクタに渡されます。

# 例

```jldoctest
julia> n, snaps, s, r = 10, 5, 0.1, 1.5;

julia> tg = rand_temporal_radius_graph(n,snaps,s,r) # 各スナップショットでの完全グラフ
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10, 10, 10, 10]
  num_edges: [90, 90, 90, 90, 90]
  num_snapshots: 5
```
