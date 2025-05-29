```
rand_temporal_hyperbolic_graph(number_nodes::Int, 
                               number_snapshots::Int;
                               α::Real,
                               R::Real,
                               speed::Real,
                               ζ::Real=1,
                               self_loop = false,
                               kws...)
```

`number_nodes` ノードと `number_snapshots` スナップショットを持つランダムな時間的グラフを作成します。最初に、ノードの位置は、パラメータ `α` に依存して、半径 `R` の円内の双曲空間で準一様分布に従って生成されます。2つのノードは、双曲距離が `R` より小さい場合に接続されます。次のスナップショットは、同じ初期分布を維持するために作成されます。

# 引数

  * `number_nodes`: 各スナップショットのノードの数。
  * `number_snapshots`: スナップショットの数。
  * `α`: 点の位置を制御するパラメータ。`α=ζ` の場合、点は半径 `R` の円上に一様に分布します。`α>ζ` の場合、点は円の中心により集中します。`α<ζ` の場合、点は円の境界により集中します。
  * `R`: 円の半径および接続の半径。
  * `speed`: ノードを更新する速度。
  * `ζ`: 円の曲率を制御するパラメータ。
  * `self_loops`: `true` の場合、ノード自身を隣接ノードとして考慮し、その場合グラフには自己ループが含まれます。
  * `kws`: さらなるキーワード引数は、各スナップショットの [`GNNGraph`](@ref) コンストラクタに渡されます。

# 例

```julia
julia> n, snaps, α, R, speed, ζ = 10, 5, 1.0, 4.0, 0.1, 1.0;

julia> thg = rand_temporal_hyperbolic_graph(n, snaps; α, R, speed, ζ)
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10, 10, 10, 10]
  num_edges: [44, 46, 48, 42, 38]
  num_snapshots: 5
```

# 参考文献

論文 [Dynamic Hidden-Variable Network Models](https://arxiv.org/pdf/2101.00414.pdf) のセクション D および論文 [Hyperbolic Geometry of Complex Networks](https://arxiv.org/pdf/1006.5169.pdf)
